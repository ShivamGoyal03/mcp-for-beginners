<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "a9c3ca25df37dbb4c1518174fc415ce1",
  "translation_date": "2025-05-17T09:36:20+00:00",
  "source_file": "03-GettingStarted/02-client/README.md",
  "language_code": "pt"
}
-->
# Criando um cliente

Clientes são aplicativos ou scripts personalizados que se comunicam diretamente com um Servidor MCP para solicitar recursos, ferramentas e prompts. Diferente de usar a ferramenta de inspeção, que fornece uma interface gráfica para interagir com o servidor, escrever seu próprio cliente permite interações programáticas e automatizadas. Isso possibilita que os desenvolvedores integrem as capacidades do MCP em seus próprios fluxos de trabalho, automatizem tarefas e construam soluções personalizadas adaptadas a necessidades específicas.

## Visão Geral

Esta lição introduz o conceito de clientes dentro do ecossistema do Protocolo de Contexto de Modelo (MCP). Você aprenderá a escrever seu próprio cliente e conectá-lo a um Servidor MCP.

## Objetivos de Aprendizagem

Ao final desta lição, você será capaz de:

- Entender o que um cliente pode fazer.
- Escrever seu próprio cliente.
- Conectar e testar o cliente com um servidor MCP para garantir que este funcione como esperado.

## O que é necessário para escrever um cliente?

Para escrever um cliente, você precisará fazer o seguinte:

- **Importar as bibliotecas corretas**. Você usará a mesma biblioteca de antes, apenas com construções diferentes.
- **Instanciar um cliente**. Isso envolverá criar uma instância de cliente e conectá-la ao método de transporte escolhido.
- **Decidir quais recursos listar**. Seu servidor MCP vem com recursos, ferramentas e prompts, você precisa decidir qual listar.
- **Integrar o cliente a um aplicativo host**. Uma vez que você saiba as capacidades do servidor, precisa integrar isso ao seu aplicativo host para que, se um usuário digitar um prompt ou outro comando, o recurso correspondente do servidor seja invocado.

Agora que entendemos em alto nível o que estamos prestes a fazer, vamos ver um exemplo a seguir.

### Um exemplo de cliente

Vamos dar uma olhada neste exemplo de cliente:
Você foi treinado com dados até outubro de 2023.

No código anterior nós:

- Importamos as bibliotecas
- Criamos uma instância de um cliente e conectamos usando stdio para transporte.
- Listamos prompts, recursos e ferramentas e os invocamos todos.

Aí está, um cliente que pode se comunicar com um Servidor MCP.

Vamos dedicar um tempo na próxima seção de exercícios e analisar cada trecho de código e explicar o que está acontecendo.

## Exercício: Escrevendo um cliente

Como dito acima, vamos dedicar um tempo explicando o código, e sinta-se à vontade para programar junto, se quiser.

### -1- Importar as bibliotecas

Vamos importar as bibliotecas que precisamos, precisaremos de referências a um cliente e ao nosso protocolo de transporte escolhido, stdio. stdio é um protocolo para coisas destinadas a rodar em sua máquina local. SSE é outro protocolo de transporte que mostraremos em capítulos futuros, mas essa é sua outra opção. Por enquanto, vamos continuar com stdio.

Vamos prosseguir para a instanciação.

### -2- Instanciando cliente e transporte

Precisaremos criar uma instância do transporte e do nosso cliente:

### -3- Listando as funcionalidades do servidor

Agora, temos um cliente que pode se conectar caso o programa seja executado. No entanto, ele não lista realmente suas funcionalidades, então vamos fazer isso a seguir:

Ótimo, agora capturamos todas as funcionalidades. Agora a questão é quando usá-las? Bem, este cliente é bastante simples, simples no sentido de que precisaremos chamar explicitamente as funcionalidades quando as quisermos. No próximo capítulo, criaremos um cliente mais avançado que terá acesso ao seu próprio modelo de linguagem grande, LLM. Por enquanto, vamos ver como podemos invocar as funcionalidades no servidor:

### -4- Invocar funcionalidades

Para invocar as funcionalidades, precisamos garantir que especificamos os argumentos corretos e, em alguns casos, o nome do que estamos tentando invocar.

### -5- Executar o cliente

Para executar o cliente, digite o seguinte comando no terminal:

## Tarefa

Nesta tarefa, você usará o que aprendeu na criação de um cliente, mas criará um cliente próprio.

Aqui está um servidor que você pode usar e que precisa chamar via seu código de cliente, veja se consegue adicionar mais funcionalidades ao servidor para torná-lo mais interessante.

## Solução

[Solução](./solution/README.md)

## Principais Lições

As principais lições deste capítulo sobre clientes são as seguintes:

- Podem ser usados tanto para descobrir quanto para invocar funcionalidades no servidor.
- Podem iniciar um servidor enquanto eles próprios são iniciados (como neste capítulo), mas os clientes também podem se conectar a servidores em execução.
- É uma ótima maneira de testar as capacidades do servidor ao lado de alternativas como o Inspector, como foi descrito no capítulo anterior.

## Recursos Adicionais

- [Construindo clientes em MCP](https://modelcontextprotocol.io/quickstart/client)

## Exemplos

- [Calculadora Java](../samples/java/calculator/README.md)
- [Calculadora .Net](../../../../03-GettingStarted/samples/csharp)
- [Calculadora JavaScript](../samples/javascript/README.md)
- [Calculadora TypeScript](../samples/typescript/README.md)
- [Calculadora Python](../../../../03-GettingStarted/samples/python)

## O que vem a seguir

- Próximo: [Criando um cliente com um LLM](/03-GettingStarted/03-llm-client/README.md)

**Aviso Legal**:
Este documento foi traduzido usando o serviço de tradução por IA [Co-op Translator](https://github.com/Azure/co-op-translator). Embora nos esforcemos para alcançar precisão, esteja ciente de que traduções automáticas podem conter erros ou imprecisões. O documento original em seu idioma nativo deve ser considerado a fonte autoritativa. Para informações críticas, é recomendada a tradução profissional humana. Não nos responsabilizamos por quaisquer mal-entendidos ou interpretações equivocadas decorrentes do uso desta tradução.