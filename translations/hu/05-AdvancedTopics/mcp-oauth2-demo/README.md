<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "bcd07a55d0e5baece8d0a1a0310fdfe6",
  "translation_date": "2025-05-17T15:44:12+00:00",
  "source_file": "05-AdvancedTopics/mcp-oauth2-demo/README.md",
  "language_code": "hu"
}
-->
# MCP OAuth2 Bemutató

Ez a projekt egy **minimális Spring Boot alkalmazás**, amely mindkettőként működik:

* egy **Spring Authorization Server** (JWT hozzáférési tokeneket bocsát ki a `client_credentials` folyamattal), és  
* egy **Resource Server** (védi a saját `/hello` végpontját).

Tükrözi a [Spring blogbejegyzésben (2025. április 2.)](https://spring.io/blog/2025/04/02/mcp-server-oauth2) bemutatott beállítást.

---

## Gyors kezdés (helyi)

```bash
# build & run
./mvnw spring-boot:run

# obtain a token
curl -u mcp-client:secret -d grant_type=client_credentials \
     http://localhost:8081/oauth2/token | jq -r .access_token > token.txt

# call the protected endpoint
curl -H "Authorization: Bearer $(cat token.txt)" http://localhost:8081/hello
```

---

## Az OAuth2 konfiguráció tesztelése

Az OAuth2 biztonsági konfigurációt a következő lépésekkel tesztelheted:

### 1. Ellenőrizd, hogy a szerver fut és védett

```bash
# This should return 401 Unauthorized, confirming OAuth2 security is active
curl -v http://localhost:8081/
```

### 2. Szerezz hozzáférési tokent kliens hitelesítő adatokkal

```bash
# Get and extract the full token response
curl -v -X POST http://localhost:8081/oauth2/token \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -H "Authorization: Basic bWNwLWNsaWVudDpzZWNyZXQ=" \
  -d "grant_type=client_credentials&scope=mcp.access"

# Or to extract just the token (requires jq)
curl -s -X POST http://localhost:8081/oauth2/token \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -H "Authorization: Basic bWNwLWNsaWVudDpzZWNyZXQ=" \
  -d "grant_type=client_credentials&scope=mcp.access" | jq -r .access_token > token.txt
```

Megjegyzés: A Basic Authentication fejléc (`bWNwLWNsaWVudDpzZWNyZXQ=`) is the Base64 encoding of `mcp-client:secret`.

### 3. Hozzáférés a védett végponthoz a token használatával

```bash
# Using the saved token
curl -H "Authorization: Bearer $(cat token.txt)" http://localhost:8081/hello

# Or directly with the token value
curl -H "Authorization: Bearer eyJra...token_value...xyz" http://localhost:8081/hello
```

Egy sikeres válasz az "Hello from MCP OAuth2 Demo!" üzenettel megerősíti, hogy az OAuth2 konfiguráció helyesen működik.

---

## Konténer építés

```bash
docker build -t mcp-oauth2-demo .
docker run -p 8081:8081 mcp-oauth2-demo
```

---

## Telepítés **Azure Container Apps**-ra

```bash
az containerapp up -n mcp-oauth2 \
  -g demo-rg -l westeurope \
  --image <your-registry>/mcp-oauth2-demo:latest \
  --ingress external --target-port 8081
```

A beérkező FQDN lesz a **issuer** (`https://<fqdn>`).  
Azure provides a trusted TLS certificate automatically for `*.azurecontainerapps.io`.

---

## Kapcsolódás **Azure API Management**-hez

Add hozzá ezt a bejövő szabályt az API-dhoz:

```xml
<inbound>
  <validate-jwt header-name="Authorization">
    <openid-config url="https://<fqdn>/.well-known/openid-configuration"/>
    <audiences>
      <audience>mcp-client</audience>
    </audiences>
  </validate-jwt>
  <base/>
</inbound>
```

Az APIM lekéri a JWKS-t és érvényesíti minden kérést.

**Felelősségkizárás**:  
Ezt a dokumentumot a [Co-op Translator](https://github.com/Azure/co-op-translator) AI fordítószolgáltatás használatával fordították le. Bár törekszünk a pontosságra, kérjük, vegye figyelembe, hogy az automatikus fordítások hibákat vagy pontatlanságokat tartalmazhatnak. Az eredeti dokumentum az anyanyelvén tekintendő hiteles forrásnak. Kritikus információk esetén javasolt a professzionális emberi fordítás. Nem vállalunk felelősséget a fordítás használatából eredő félreértésekért vagy félreértelmezésekért.