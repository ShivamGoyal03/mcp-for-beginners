<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "f01d4263fc6eec331615fef42429b720",
  "translation_date": "2025-06-18T18:15:56+00:00",
  "source_file": "03-GettingStarted/01-first-server/README.md",
  "language_code": "mo"
}
-->
### -2- 建立專案

既然你已經安裝好 SDK，接下來讓我們建立一個專案：

### -3- 建立專案檔案

### -4- 撰寫伺服器程式碼

### -5- 新增工具與資源

透過加入以下程式碼，新增一個工具和一個資源：

### -6 最終程式碼

讓我們加入最後所需的程式碼，讓伺服器可以啟動：

### -7- 測試伺服器

使用以下指令啟動伺服器：

### -8- 使用 Inspector 執行

Inspector 是一個很棒的工具，可以啟動你的伺服器，並讓你與它互動，測試它是否正常運作。讓我們啟動它：

> [!NOTE]
> 「指令」欄位中的內容可能會有所不同，因為它包含了用你所選擇的執行環境來執行伺服器的指令。

你應該會看到以下使用者介面：

![Connect](../../../../translated_images/connect.141db0b2bd05f096fb1dd91273771fd8b2469d6507656c3b0c9df4b3c5473929.mo.png)

1. 按下「Connect」按鈕連接到伺服器  
   連接成功後，你應該會看到以下畫面：

   ![Connected](../../../../translated_images/connected.73d1e042c24075d386cacdd4ee7cd748c16364c277d814e646ff2f7b5eefde85.mo.png)

2. 選擇「Tools」並點擊「listTools」，你會看到「Add」出現，點選「Add」並填入參數值。

   你應該會看到以下回應，也就是「add」工具的結果：

   ![Result of running add](../../../../translated_images/ran-tool.a5a6ee878c1369ec1e379b81053395252a441799dbf23416c36ddf288faf8249.mo.png)

恭喜你，成功建立並執行了你的第一個伺服器！

### 官方 SDK

MCP 提供多種語言的官方 SDK：

- [C# SDK](https://github.com/modelcontextprotocol/csharp-sdk) - 與 Microsoft 共同維護
- [Java SDK](https://github.com/modelcontextprotocol/java-sdk) - 與 Spring AI 共同維護
- [TypeScript SDK](https://github.com/modelcontextprotocol/typescript-sdk) - 官方 TypeScript 實作
- [Python SDK](https://github.com/modelcontextprotocol/python-sdk) - 官方 Python 實作
- [Kotlin SDK](https://github.com/modelcontextprotocol/kotlin-sdk) - 官方 Kotlin 實作
- [Swift SDK](https://github.com/modelcontextprotocol/swift-sdk) - 與 Loopwork AI 共同維護
- [Rust SDK](https://github.com/modelcontextprotocol/rust-sdk) - 官方 Rust 實作

## 重要重點

- 使用語言專用的 SDK，設定 MCP 開發環境相當簡單
- 建立 MCP 伺服器需建立並註冊具明確結構的工具
- 測試與除錯是確保 MCP 實作穩定可靠的關鍵

## 範例

- [Java 計算機](../samples/java/calculator/README.md)
- [.Net 計算機](../../../../03-GettingStarted/samples/csharp)
- [JavaScript 計算機](../samples/javascript/README.md)
- [TypeScript 計算機](../samples/typescript/README.md)
- [Python 計算機](../../../../03-GettingStarted/samples/python)

## 作業

建立一個簡單的 MCP 伺服器，並加入你選擇的工具：

1. 使用你偏好的語言（.NET、Java、Python 或 JavaScript）實作該工具。
2. 定義輸入參數和回傳值。
3. 使用 Inspector 工具確保伺服器運作正常。
4. 用各種輸入測試實作。

## 解答

[解答](./solution/README.md)

## 其他資源

- [使用 Model Context Protocol 在 Azure 上建立代理](https://learn.microsoft.com/azure/developer/ai/intro-agents-mcp)
- [使用 Azure Container Apps 遠端 MCP (Node.js/TypeScript/JavaScript)](https://learn.microsoft.com/samples/azure-samples/mcp-container-ts/mcp-container-ts/)
- [.NET OpenAI MCP 代理](https://learn.microsoft.com/samples/azure-samples/openai-mcp-agent-dotnet/openai-mcp-agent-dotnet/)

## 接下來的步驟

下一章節：[MCP 用戶端入門](/03-GettingStarted/02-client/README.md)

**免責聲明**：  
本文件係使用 AI 翻譯服務 [Co-op Translator](https://github.com/Azure/co-op-translator) 進行翻譯。雖然我們力求準確，但請注意自動翻譯可能包含錯誤或不準確之處。原始文件之母語版本應視為權威來源。對於重要資訊，建議採用專業人工翻譯。我們不對因使用本翻譯所產生之任何誤解或誤釋負責。