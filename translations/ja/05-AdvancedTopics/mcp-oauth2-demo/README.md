<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "0a7083e660ca0d85fd6a947514c61993",
  "translation_date": "2025-06-12T21:37:03+00:00",
  "source_file": "05-AdvancedTopics/mcp-oauth2-demo/README.md",
  "language_code": "ja"
}
-->
# MCP OAuth2 デモ

このプロジェクトは、**最小限の Spring Boot アプリケーション**で、以下の両方の役割を果たします：

* **Spring Authorization Server**（`client_credentials` フローを使って JWT アクセストークンを発行）  
* **Resource Server**（自身の `/hello` エンドポイントを保護）

[Spring ブログ記事 (2025年4月2日)](https://spring.io/blog/2025/04/02/mcp-server-oauth2) で紹介されている構成を再現しています。

---

## クイックスタート（ローカル）

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

## OAuth2 設定のテスト

以下の手順で OAuth2 のセキュリティ設定をテストできます：

### 1. サーバーが起動してセキュアになっていることを確認

```bash
# This should return 401 Unauthorized, confirming OAuth2 security is active
curl -v http://localhost:8081/
```

### 2. クライアント認証情報を使ってアクセストークンを取得

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

補足：Basic 認証ヘッダーは `bWNwLWNsaWVudDpzZWNyZXQ=`) is the Base64 encoding of `mcp-client:secret` です。

### 3. トークンを使って保護されたエンドポイントにアクセス

```bash
# Using the saved token
curl -H "Authorization: Bearer $(cat token.txt)" http://localhost:8081/hello

# Or directly with the token value
curl -H "Authorization: Bearer eyJra...token_value...xyz" http://localhost:8081/hello
```

"Hello from MCP OAuth2 Demo!" の成功レスポンスが返れば、OAuth2 の設定が正しく動作していることが確認できます。

---

## コンテナのビルド

```bash
docker build -t mcp-oauth2-demo .
docker run -p 8081:8081 mcp-oauth2-demo
```

---

## **Azure Container Apps** へのデプロイ

```bash
az containerapp up -n mcp-oauth2 \
  -g demo-rg -l westeurope \
  --image <your-registry>/mcp-oauth2-demo:latest \
  --ingress external --target-port 8081
```

ingress の FQDN があなたの **issuer** になります（`https://<fqdn>`).  
Azure provides a trusted TLS certificate automatically for `*.azurecontainerapps.io`）。

---

## **Azure API Management** との連携

API に以下のインバウンドポリシーを追加してください：

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

APIM は JWKS を取得し、すべてのリクエストを検証します。

---

## 次にやること

- [5.4 ルートコンテキスト](../mcp-root-contexts/README.md)

**免責事項**:  
本書類はAI翻訳サービス「Co-op Translator」（https://github.com/Azure/co-op-translator）を使用して翻訳されています。正確性を期していますが、自動翻訳には誤りや不正確な部分が含まれる可能性があることをご承知ください。原文はあくまで正式な情報源とみなされるべきです。重要な情報については、専門の人間翻訳を推奨します。本翻訳の利用により生じた誤解や誤訳について、一切の責任を負いかねます。