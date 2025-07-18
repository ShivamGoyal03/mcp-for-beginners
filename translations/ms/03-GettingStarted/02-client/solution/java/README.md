<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "7074b9f4c8cd147c1c10f569d8508c82",
  "translation_date": "2025-06-11T13:14:22+00:00",
  "source_file": "03-GettingStarted/02-client/solution/java/README.md",
  "language_code": "ms"
}
-->
# MCP Java Client - דוגמת מחשבון

פרויקט זה מדגים כיצד ליצור לקוח Java שמתחבר לשרת MCP (Model Context Protocol) ומבצע איתו אינטראקציה. בדוגמה זו, נתחבר לשרת המחשבון מפרק 01 ונבצע פעולות מתמטיות שונות.

## דרישות מוקדמות

לפני הרצת הלקוח, יש לבצע את הפעולות הבאות:

1. **הפעל את שרת המחשבון** מפרק 01:
   - נווט לתיקיית שרת המחשבון: `03-GettingStarted/01-first-server/solution/java/`
   - בנייה והרצת שרת המחשבון:
     ```cmd
     cd ..\01-first-server\solution\java
     .\mvnw clean install -DskipTests
     java -jar target\calculator-server-0.0.1-SNAPSHOT.jar
     ```
   - השרת אמור לפעול בכתובת `http://localhost:8080`

2. **Java 21 or higher** installed on your system
3. **Maven** (included via Maven Wrapper)

## What is the SDKClient?

The `SDKClient` היא אפליקציית Java שמדגימה כיצד:
- להתחבר לשרת MCP באמצעות Server-Sent Events (SSE)
- לרשום את הכלים הזמינים מהשרת
- לקרוא לפונקציות מחשבון שונות מרחוק
- לטפל בתגובות ולהציג תוצאות

## כיצד זה עובד

הלקוח משתמש במסגרת Spring AI MCP כדי:

1. **להקים חיבור**: יוצר לקוח WebFlux SSE שמתחבר לשרת המחשבון
2. **אתחול הלקוח**: מגדיר את לקוח MCP ומקים את החיבור
3. **גילוי כלים**: מציג את כל פעולות המחשבון הזמינות
4. **ביצוע פעולות**: קורא לפונקציות מתמטיות שונות עם נתוני דוגמה
5. **הצגת תוצאות**: מציג את תוצאות כל חישוב

## מבנה הפרויקט

```
src/
└── main/
    └── java/
        └── com/
            └── microsoft/
                └── mcp/
                    └── sample/
                        └── client/
                            └── SDKClient.java    # Main client implementation
```

## תלות מרכזית

הפרויקט משתמש בתלותות המרכזיות הבאות:

```xml
<dependency>
    <groupId>org.springframework.ai</groupId>
    <artifactId>spring-ai-starter-mcp-server-webflux</artifactId>
</dependency>
```

תלות זו מספקת:
- `McpClient` - The main client interface
- `WebFluxSseClientTransport` - תחבורה מסוג SSE לתקשורת מבוססת רשת
- סכמות פרוטוקול MCP וסוגי בקשות/תגובות

## בניית הפרויקט

בנה את הפרויקט באמצעות Maven wrapper:

```cmd
.\mvnw clean install
```

## הרצת הלקוח

```cmd
java -jar .\target\calculator-client-0.0.1-SNAPSHOT.jar
```

**הערה**: ודא ששרת המחשבון פועל בכתובת `http://localhost:8080` before executing any of these commands.

## What the Client Does

When you run the client, it will:

1. **Connect** to the calculator server at `http://localhost:8080`
2. **רשימת כלים** - מציג את כל פעולות המחשבון הזמינות
3. **ביצוע חישובים**:
   - חיבור: 5 + 3 = 8
   - חיסור: 10 - 4 = 6
   - כפל: 6 × 7 = 42
   - חילוק: 20 ÷ 4 = 5
   - חזקה: 2^8 = 256
   - שורש ריבועי: √16 = 4
   - ערך מוחלט: |-5.5| = 5.5
   - עזרה: מציג את הפעולות הזמינות

## פלט צפוי

```
Available Tools = ListToolsResult[tools=[Tool[name=add, description=Add two numbers together, ...], ...]]
Add Result = CallToolResult[content=[TextContent[text="5,00 + 3,00 = 8,00"]], isError=false]
Subtract Result = CallToolResult[content=[TextContent[text="10,00 - 4,00 = 6,00"]], isError=false]
Multiply Result = CallToolResult[content=[TextContent[text="6,00 * 7,00 = 42,00"]], isError=false]
Divide Result = CallToolResult[content=[TextContent[text="20,00 / 4,00 = 5,00"]], isError=false]
Power Result = CallToolResult[content=[TextContent[text="2,00 ^ 8,00 = 256,00"]], isError=false]
Square Root Result = CallToolResult[content=[TextContent[text="√16,00 = 4,00"]], isError=false]
Absolute Result = CallToolResult[content=[TextContent[text="|-5,50| = 5,50"]], isError=false]
Help = CallToolResult[content=[TextContent[text="Basic Calculator MCP Service\n\nAvailable operations:\n1. add(a, b) - Adds two numbers\n2. subtract(a, b) - Subtracts the second number from the first\n..."]], isError=false]
```

**הערה**: ייתכן שתקבל אזהרות Maven לגבי תהליכים שנותרו בסיום - זה נורמלי באפליקציות ריאקטיביות ואינו מצביע על שגיאה.

## הבנת הקוד

### 1. הגדרת התחבורה
```java
var transport = new WebFluxSseClientTransport(WebClient.builder().baseUrl("http://localhost:8080"));
```
זה יוצר תחבורה מסוג SSE (Server-Sent Events) שמתחברת לשרת המחשבון.

### 2. יצירת הלקוח
```java
var client = McpClient.sync(this.transport).build();
client.initialize();
```
יוצר לקוח MCP סינכרוני ומאתחל את החיבור.

### 3. קריאת כלים
```java
CallToolResult resultAdd = client.callTool(new CallToolRequest("add", Map.of("a", 5.0, "b", 3.0)));
```
קורא לכלי "add" עם הפרמטרים a=5.0 ו- b=3.0.

## פתרון תקלות

### השרת לא פועל
אם מתקבלות שגיאות חיבור, ודא ששרת המחשבון מפרק 01 פועל:
```
Error: Connection refused
```
**פתרון**: הפעל את שרת המחשבון קודם.

### פורט בשימוש
אם הפורט 8080 תפוס:
```
Error: Address already in use
```
**פתרון**: עצור אפליקציות אחרות שמשתמשות בפורט 8080 או שנה את הפורט בשרת.

### שגיאות בנייה
אם מתקבלות שגיאות בנייה:
```cmd
.\mvnw clean install -DskipTests
```

## למידה נוספת

- [Spring AI MCP Documentation](https://docs.spring.io/spring-ai/reference/api/mcp/)
- [Model Context Protocol Specification](https://modelcontextprotocol.io/)
- [Spring WebFlux Documentation](https://docs.spring.io/spring-framework/docs/current/reference/html/web-reactive.html)

**Penafian**:  
Dokumen ini telah diterjemahkan menggunakan perkhidmatan terjemahan AI [Co-op Translator](https://github.com/Azure/co-op-translator). Walaupun kami berusaha untuk ketepatan, sila ambil perhatian bahawa terjemahan automatik mungkin mengandungi kesilapan atau ketidaktepatan. Dokumen asal dalam bahasa asalnya harus dianggap sebagai sumber yang sahih. Untuk maklumat penting, terjemahan profesional oleh manusia adalah disyorkan. Kami tidak bertanggungjawab atas sebarang salah faham atau salah tafsir yang timbul daripada penggunaan terjemahan ini.