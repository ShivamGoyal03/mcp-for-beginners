<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "4d3415b9d2bf58bc69be07f945a69e07",
  "translation_date": "2025-05-20T23:34:57+00:00",
  "source_file": "09-CaseStudy/README.md",
  "language_code": "ja"
}
-->
# ケーススタディ：Azure AI Travel Agents – 参照実装

## 概要

[Azure AI Travel Agents](https://github.com/Azure-Samples/azure-ai-travel-agents) は、Microsoft が開発した包括的な参照ソリューションで、Model Context Protocol（MCP）、Azure OpenAI、Azure AI Search を活用してマルチエージェントのAI搭載旅行プランニングアプリケーションを構築する方法を示しています。このプロジェクトは、複数のAIエージェントのオーケストレーション、企業データの統合、現実的なシナリオに対応した安全で拡張可能なプラットフォームの提供に関するベストプラクティスを紹介します。

## 主な特徴
- **マルチエージェントのオーケストレーション：** MCPを使って、フライト、ホテル、旅程などの専門エージェントを調整し、複雑な旅行プランニングのタスクを協力して実行します。
- **企業データの統合：** Azure AI Search やその他の企業データソースに接続し、最新かつ関連性の高い旅行情報を提供します。
- **安全でスケーラブルなアーキテクチャ：** Azureサービスを活用し、認証・認可を行い、企業のセキュリティベストプラクティスに則ったスケーラブルな展開を実現します。
- **拡張可能なツール群：** 再利用可能なMCPツールやプロンプトテンプレートを実装し、新しいドメインやビジネス要件に迅速に対応可能です。
- **ユーザー体験：** Azure OpenAI と MCP による会話型インターフェースを提供し、ユーザーが旅行エージェントと対話できるようにします。

## アーキテクチャ
![Architecture](https://raw.githubusercontent.com/Azure-Samples/azure-ai-travel-agents/main/docs/ai-travel-agents-architecture-diagram.png)

### アーキテクチャ図の説明

Azure AI Travel Agents ソリューションは、モジュール性、スケーラビリティ、複数のAIエージェントと企業データソースの安全な統合を考慮して設計されています。主なコンポーネントとデータフローは以下の通りです：

- **ユーザーインターフェース：** ユーザーは会話型UI（ウェブチャットやTeamsボットなど）を通じてシステムとやり取りし、問い合わせや旅行のおすすめを受け取ります。
- **MCPサーバー：** 中央のオーケストレーターとして機能し、ユーザー入力を受け取り、コンテキストを管理し、Model Context Protocol を介して専門エージェント（FlightAgent、HotelAgent、ItineraryAgentなど）の動作を調整します。
- **AIエージェント：** 各エージェントは特定のドメイン（フライト、ホテル、旅程）を担当し、MCPツールとして実装されています。プロンプトテンプレートやロジックを用いてリクエストを処理し、応答を生成します。
- **Azure OpenAI サービス：** 高度な自然言語理解と生成を提供し、エージェントがユーザーの意図を解釈し、会話的な応答を生成できるようにします。
- **Azure AI Search & 企業データ：** エージェントは Azure AI Search やその他の企業データソースに問い合わせて、最新のフライト、ホテル、旅行オプションの情報を取得します。
- **認証とセキュリティ：** Microsoft Entra ID と連携し、安全な認証を行い、すべてのリソースに最小権限のアクセス制御を適用します。
- **デプロイメント：** Azure Container Apps 上での展開を想定し、スケーラビリティ、監視、運用効率を確保します。

このアーキテクチャにより、複数のAIエージェントのシームレスなオーケストレーション、企業データとの安全な統合、ドメイン固有のAIソリューション構築のための堅牢で拡張性の高いプラットフォームを実現しています。

## アーキテクチャ図のステップごとの説明
大きな旅行を計画するときに、専門家のチームが細部までサポートしてくれると想像してください。Azure AI Travel Agents システムも同様に、各部分（チームメンバーのような）がそれぞれの役割を持って動作します。全体の流れは以下の通りです：

### ユーザーインターフェース（UI）：
これは旅行代理店の受付のようなものです。ユーザーはここで「パリ行きのフライトを探して」といった質問やリクエストを行います。ウェブサイトのチャットウィンドウやメッセージングアプリが該当します。

### MCPサーバー（コーディネーター）：
MCPサーバーは受付のマネージャーのような役割で、あなたのリクエストを聞いて、どの専門家が担当すべきかを決めます。会話の流れを管理し、全体がスムーズに進むよう調整します。

### AIエージェント（専門アシスタント）：
各エージェントは特定分野の専門家です。あるエージェントはフライトに詳しく、別のエージェントはホテルに精通し、また別のエージェントは旅程の計画を担当します。リクエストが来ると、MCPサーバーが適切なエージェントに振り分け、彼らは知識とツールを使って最適な選択肢を提案します。

### Azure OpenAI サービス（言語の専門家）：
言い回しがどうであれ、あなたの意図を正確に理解する言語の専門家のような存在です。エージェントがリクエストを理解し、自然で会話的な応答を生成するのを助けます。

### Azure AI Search & 企業データ（情報ライブラリ）：
最新の旅行情報（フライトスケジュールやホテルの空き状況など）が揃った巨大な図書館のようなものです。エージェントはここを検索して、最も正確な情報を引き出します。

### 認証とセキュリティ（警備員）：
特定のエリアに入れる人をチェックする警備員のように、許可された人やエージェントだけが機密情報にアクセスできるようにします。データの安全とプライバシーを守ります。

### Azure Container Apps 上のデプロイメント（建物）：
これらのアシスタントやツールは、安全でスケーラブルな建物（クラウド）内で連携しています。つまり、多くのユーザーを同時に処理でき、いつでも利用可能な状態です。

## 全体の流れ：

受付（UI）で質問を始めます。  
マネージャー（MCPサーバー）がどの専門家（エージェント）に頼むかを判断します。  
専門家は言語の専門家（OpenAI）を使ってリクエストを理解し、情報ライブラリ（AI Search）から最適な答えを探します。  
警備員（認証）が安全を確保します。  
これらすべてが信頼性が高くスケーラブルな建物（Azure Container Apps）内で行われるため、快適かつ安全な体験が提供されます。  
このチームワークにより、まるで専門家の旅行代理店チームが一緒に働くかのように、迅速かつ安全に旅行計画をサポートします。

## 技術的実装
- **MCPサーバー：** コアのオーケストレーションロジックをホストし、エージェントツールを公開し、マルチステップの旅行プランニングワークフローのコンテキストを管理します。
- **エージェント：** 各エージェント（例：FlightAgent、HotelAgent）は独自のプロンプトテンプレートとロジックを持つMCPツールとして実装されています。
- **Azure連携：** 自然言語理解には Azure OpenAI を、データ取得には Azure AI Search を利用します。
- **セキュリティ：** Microsoft Entra ID と連携し、すべてのリソースに最小権限のアクセス制御を適用します。
- **デプロイメント：** スケーラビリティと運用効率のために Azure Container Apps への展開をサポートします。

## 結果と影響
- MCPを活用して複数のAIエージェントを実運用レベルでオーケストレーションする方法を実証しています。
- エージェントの調整、データ統合、安全な展開のための再利用可能なパターンを提供し、ソリューション開発を加速します。
- MCPとAzureサービスを使ったドメイン固有のAIアプリケーション構築のための設計図として機能します。

## 参考資料
- [Azure AI Travel Agents GitHubリポジトリ](https://github.com/Azure-Samples/azure-ai-travel-agents)
- [Azure OpenAI サービス](https://azure.microsoft.com/en-us/products/ai-services/openai-service/)
- [Azure AI Search](https://azure.microsoft.com/en-us/products/ai-services/ai-search/)
- [Model Context Protocol (MCP)](https://modelcontextprotocol.io/)

**免責事項**：  
本書類はAI翻訳サービス[Co-op Translator](https://github.com/Azure/co-op-translator)を使用して翻訳されています。正確性の向上に努めておりますが、自動翻訳には誤りや不正確な部分が含まれる可能性があります。原文の言語によるオリジナル文書が正式な情報源とみなされるべきです。重要な情報については、専門の人間による翻訳を推奨します。本翻訳の使用により生じた誤解や誤訳について、一切の責任を負いかねますのでご了承ください。