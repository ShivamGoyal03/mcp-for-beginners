<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "5331ffd328a54b90f76706c52b673e27",
  "translation_date": "2025-05-29T20:22:47+00:00",
  "source_file": "03-GettingStarted/01-first-server/README.md",
  "language_code": "br"
}
-->
### -2- Criar projeto

Agora que você instalou seu SDK, vamos criar um projeto a seguir:

### -3- Criar arquivos do projeto

### -4- Criar código do servidor

### -5- Adicionando uma ferramenta e um recurso

Adicione uma ferramenta e um recurso inserindo o seguinte código:

### -6 Código final

Vamos adicionar o código final necessário para que o servidor possa iniciar:

### -7- Testar o servidor

Inicie o servidor com o seguinte comando:

### -8- Executar usando o inspector

O inspector é uma ótima ferramenta que pode iniciar seu servidor e permitir que você interaja com ele para testar seu funcionamento. Vamos iniciá-lo:

> [!NOTE]
> pode parecer diferente no campo "command" pois contém o comando para rodar um servidor com seu runtime específico/

Você deverá ver a seguinte interface de usuário:

![Connect](../../../../translated_images/connect.141db0b2bd05f096fb1dd91273771fd8b2469d6507656c3b0c9df4b3c5473929.br.png)

1. Conecte-se ao servidor selecionando o botão Connect  
   Após conectar ao servidor, você verá o seguinte:

   ![Connected](../../../../translated_images/connected.73d1e042c24075d386cacdd4ee7cd748c16364c277d814e646ff2f7b5eefde85.br.png)

2. Selecione "Tools" e "listTools", você deverá ver "Add" aparecer, selecione "Add" e preencha os valores dos parâmetros.

   Você verá a seguinte resposta, ou seja, o resultado da ferramenta "add":

   ![Result of running add](../../../../translated_images/ran-tool.a5a6ee878c1369ec1e379b81053395252a441799dbf23416c36ddf288faf8249.br.png)

Parabéns, você conseguiu criar e executar seu primeiro servidor!

### SDKs oficiais

O MCP oferece SDKs oficiais para várias linguagens:
- [C# SDK](https://github.com/modelcontextprotocol/csharp-sdk) - Mantido em colaboração com a Microsoft
- [Java SDK](https://github.com/modelcontextprotocol/java-sdk) - Mantido em colaboração com a Spring AI
- [TypeScript SDK](https://github.com/modelcontextprotocol/typescript-sdk) - Implementação oficial em TypeScript
- [Python SDK](https://github.com/modelcontextprotocol/python-sdk) - Implementação oficial em Python
- [Kotlin SDK](https://github.com/modelcontextprotocol/kotlin-sdk) - Implementação oficial em Kotlin
- [Swift SDK](https://github.com/modelcontextprotocol/swift-sdk) - Mantido em colaboração com a Loopwork AI
- [Rust SDK](https://github.com/modelcontextprotocol/rust-sdk) - Implementação oficial em Rust

## Principais pontos

- Configurar o ambiente de desenvolvimento MCP é simples com SDKs específicos para cada linguagem
- Construir servidores MCP envolve criar e registrar ferramentas com esquemas claros
- Testar e depurar são essenciais para implementações MCP confiáveis

## Exemplos

- [Java Calculator](../samples/java/calculator/README.md)
- [.Net Calculator](../../../../03-GettingStarted/samples/csharp)
- [JavaScript Calculator](../samples/javascript/README.md)
- [TypeScript Calculator](../samples/typescript/README.md)
- [Python Calculator](../../../../03-GettingStarted/samples/python)

## Exercício

Crie um servidor MCP simples com uma ferramenta de sua escolha:
1. Implemente a ferramenta na sua linguagem preferida (.NET, Java, Python ou JavaScript).
2. Defina os parâmetros de entrada e os valores de retorno.
3. Execute a ferramenta inspector para garantir que o servidor funcione como esperado.
4. Teste a implementação com diferentes entradas.

## Solução

[Solution](./solution/README.md)

## Recursos adicionais

- [Repositório MCP no GitHub](https://github.com/microsoft/mcp-for-beginners)

## Próximos passos

Próximo: [Começando com Clientes MCP](/03-GettingStarted/02-client/README.md)

**Aviso Legal**:  
Este documento foi traduzido usando o serviço de tradução por IA [Co-op Translator](https://github.com/Azure/co-op-translator). Embora nos esforcemos para garantir a precisão, esteja ciente de que traduções automáticas podem conter erros ou imprecisões. O documento original em seu idioma nativo deve ser considerado a fonte oficial. Para informações críticas, recomenda-se a tradução profissional humana. Não nos responsabilizamos por quaisquer mal-entendidos ou interpretações incorretas decorrentes do uso desta tradução.