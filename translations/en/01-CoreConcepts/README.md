<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "4bf553c18e7e226c3d76ab0cde627d26",
  "translation_date": "2025-05-20T20:06:29+00:00",
  "source_file": "01-CoreConcepts/README.md",
  "language_code": "en"
}
-->
# 📖 MCP Core Concepts: Mastering the Model Context Protocol for AI Integration

The Model Context Protocol (MCP) is a powerful, standardized framework that streamlines communication between Large Language Models (LLMs) and external tools, applications, and data sources. This SEO-optimized guide will take you through the core concepts of MCP, helping you understand its client-server architecture, key components, communication processes, and best practices for implementation.

## Overview

This lesson covers the fundamental architecture and components that form the Model Context Protocol (MCP) ecosystem. You'll learn about the client-server setup, main elements, and communication methods that enable MCP interactions.

## 👩‍🎓 Key Learning Objectives

By the end of this lesson, you will:

- Understand the MCP client-server architecture.
- Identify the roles and responsibilities of Hosts, Clients, and Servers.
- Analyze the core features that make MCP a flexible integration layer.
- Learn how information flows within the MCP ecosystem.
- Gain practical insights through code examples in .NET, Java, Python, and JavaScript.

## 🔎 MCP Architecture: A Closer Look

The MCP ecosystem is based on a client-server model. This modular design allows AI applications to efficiently interact with tools, databases, APIs, and contextual resources. Let's break down this architecture into its key components.

### 1. Hosts

In the Model Context Protocol (MCP), Hosts serve as the main interface through which users engage with the protocol. Hosts are applications or environments that initiate connections with MCP servers to access data, tools, and prompts. Examples include integrated development environments (IDEs) like Visual Studio Code, AI tools like Claude Desktop, or custom agents designed for specific tasks.

**Hosts** are LLM applications that start connections. They:

- Run or interact with AI models to generate responses.
- Initiate connections with MCP servers.
- Manage conversation flow and user interfaces.
- Control permissions and security settings.
- Handle user consent for data sharing and tool execution.

### 2. Clients

Clients are crucial components that enable interaction between Hosts and MCP servers. Acting as intermediaries, Clients allow Hosts to access and use the functionalities provided by MCP servers. They play a vital role in ensuring smooth communication and efficient data exchange within the MCP architecture.

**Clients** are connectors inside the host application. They:

- Send requests to servers with prompts or instructions.
- Negotiate capabilities with servers.
- Manage tool execution requests from models.
- Process and display responses to users.

### 3. Servers

Servers handle requests from MCP clients and provide appropriate responses. They manage tasks such as data retrieval, tool execution, and prompt generation. Servers ensure communication between clients and Hosts is efficient and reliable, maintaining the integrity of the interaction.

**Servers** are services that provide context and capabilities. They:

- Register available features (resources, prompts, tools).
- Receive and execute tool calls from clients.
- Provide contextual information to improve model responses.
- Return outputs back to clients.
- Maintain state across interactions when needed.

Anyone can develop servers to extend model capabilities with specialized functions.

### 4. Server Features

Servers in the Model Context Protocol (MCP) offer foundational building blocks that enable rich interactions among clients, hosts, and language models. These features enhance MCP by providing structured context, tools, and prompts.

MCP servers can provide any of the following features:

#### 📑 Resources 

Resources in MCP include various types of context and data that users or AI models can use. These include:

- **Contextual Data**: Information and context that help users or AI models make decisions and complete tasks.
- **Knowledge Bases and Document Repositories**: Collections of structured and unstructured data such as articles, manuals, and research papers that offer valuable insights.
- **Local Files and Databases**: Data stored locally on devices or within databases, accessible for processing and analysis.
- **APIs and Web Services**: External interfaces and services that provide additional data and functions, enabling integration with various online resources and tools.

An example of a resource could be a database schema or a file accessed like this:

```text
file://log.txt
database://schema
```

### 🤖 Prompts

Prompts in MCP include predefined templates and interaction patterns designed to streamline workflows and improve communication. These include:

- **Templated Messages and Workflows**: Pre-structured messages and processes that guide users through specific tasks.
- **Predefined Interaction Patterns**: Standard sequences of actions and responses that ensure consistent and efficient communication.
- **Specialized Conversation Templates**: Customizable templates tailored for specific conversation types, ensuring relevant and context-aware interactions.

A prompt template might look like this:

```markdown
Generate a product slogan based on the following {{product}} with the following {{keywords}}
```

#### ⛏️ Tools

Tools in MCP are functions the AI model can execute to perform specific tasks. These tools enhance the AI model’s capabilities by providing structured and reliable operations. Key aspects include:

- **Functions for the AI model to execute**: Tools are executable functions the AI model can call to perform tasks.
- **Unique Name and Description**: Each tool has a distinct name and a detailed description explaining its purpose.
- **Parameters and Outputs**: Tools accept specific parameters and return structured outputs for consistent results.
- **Discrete Functions**: Tools perform distinct tasks such as web searches, calculations, and database queries.

An example tool might look like this:

```typescript
server.tool(
  "GetProducts",
  {
    pageSize: z.string().optional(),
    pageCount: z.string().optional()
  }, () => {
    // return results from API
  }
)
```

## Client Features

In MCP, clients offer several important features to servers, enhancing overall functionality and interaction. One notable feature is Sampling.

### 👉 Sampling

- **Server-Initiated Agentic Behaviors**: Clients allow servers to autonomously initiate specific actions or behaviors, increasing system dynamism.
- **Recursive LLM Interactions**: This enables recursive interactions with large language models (LLMs), supporting more complex and iterative task processing.
- **Requesting Additional Model Completions**: Servers can ask for additional completions from the model to ensure thorough and contextually relevant responses.

## Information Flow in MCP

MCP defines a structured flow of information between hosts, clients, servers, and models. Understanding this flow clarifies how user requests are processed and how external tools and data are integrated into model responses.

- **Host Initiates Connection**  
  The host application (such as an IDE or chat interface) establishes a connection to an MCP server, typically via STDIO, WebSocket, or another supported transport.

- **Capability Negotiation**  
  The client (embedded in the host) and the server exchange information about their supported features, tools, resources, and protocol versions to ensure mutual understanding of available capabilities.

- **User Request**  
  The user interacts with the host (e.g., enters a prompt or command). The host gathers this input and passes it to the client for processing.

- **Resource or Tool Use**  
  - The client may request additional context or resources from the server (such as files, database entries, or knowledge base articles) to enrich the model's understanding.  
  - If the model decides a tool is needed (e.g., to fetch data, perform a calculation, or call an API), the client sends a tool invocation request to the server, specifying the tool name and parameters.

- **Server Execution**  
  The server receives the resource or tool request, executes the necessary operations (such as running a function, querying a database, or retrieving a file), and returns the results to the client in a structured format.

- **Response Generation**  
  The client integrates the server's responses (resource data, tool outputs, etc.) into the ongoing model interaction. The model uses this information to generate a comprehensive and contextually relevant response.

- **Result Presentation**  
  The host receives the final output from the client and presents it to the user, often including both the model's generated text and any results from tool executions or resource lookups.

This flow enables MCP to support advanced, interactive, and context-aware AI applications by seamlessly connecting models with external tools and data sources.

## Protocol Details

MCP (Model Context Protocol) is built on top of [JSON-RPC 2.0](https://www.jsonrpc.org/), providing a standardized, language-agnostic message format for communication between hosts, clients, and servers. This foundation enables reliable, structured, and extensible interactions across diverse platforms and programming languages.

### Key Protocol Features

MCP extends JSON-RPC 2.0 with additional conventions for tool invocation, resource access, and prompt management. It supports multiple transport layers (STDIO, WebSocket, SSE) and enables secure, extensible, and language-agnostic communication between components.

#### 🧢 Base Protocol

- **JSON-RPC Message Format**: All requests and responses follow the JSON-RPC 2.0 specification, ensuring a consistent structure for method calls, parameters, results, and error handling.
- **Stateful Connections**: MCP sessions maintain state across multiple requests, supporting ongoing conversations, context accumulation, and resource management.
- **Capability Negotiation**: During connection setup, clients and servers exchange information about supported features, protocol versions, available tools, and resources. This ensures both sides understand each other's capabilities and can adapt accordingly.

#### ➕ Additional Utilities

Here are some extra utilities and protocol extensions MCP offers to improve developer experience and enable advanced scenarios:

- **Configuration Options**: MCP allows dynamic configuration of session parameters, such as tool permissions, resource access, and model settings, tailored to each interaction.
- **Progress Tracking**: Long-running operations can report progress updates, enabling responsive user interfaces and better user experience during complex tasks.
- **Request Cancellation**: Clients can cancel ongoing requests, allowing users to interrupt operations that are no longer needed or taking too long.
- **Error Reporting**: Standardized error messages and codes help diagnose issues, handle failures gracefully, and provide actionable feedback to users and developers.
- **Logging**: Both clients and servers can emit structured logs for auditing, debugging, and monitoring protocol interactions.

By leveraging these protocol features, MCP ensures robust, secure, and flexible communication between language models and external tools or data sources.

### 🔐 Security Considerations

MCP implementations should follow several key security principles to ensure safe and trustworthy interactions:

- **User Consent and Control**: Users must explicitly consent before any data is accessed or operations performed. They should have clear control over what data is shared and which actions are authorized, supported by intuitive user interfaces for reviewing and approving activities.

- **Data Privacy**: User data should only be exposed with explicit consent and protected by appropriate access controls. MCP implementations must prevent unauthorized data transmission and maintain privacy throughout all interactions.

- **Tool Safety**: Before invoking any tool, explicit user consent is required. Users should clearly understand each tool’s functionality, and strong security boundaries must be enforced to prevent unintended or unsafe tool execution.

By adhering to these principles, MCP ensures user trust, privacy, and safety across all protocol interactions.

## Code Examples: Key Components

Below are code examples in popular programming languages demonstrating how to implement key MCP server components and tools.

### .NET Example: Creating a Simple MCP Server with Tools

This practical .NET example shows how to implement a simple MCP server with custom tools. It covers defining and registering tools, handling requests, and connecting the server using the Model Context Protocol.

```csharp
using System;
using System.Threading.Tasks;
using ModelContextProtocol.Server;
using ModelContextProtocol.Server.Transport;
using ModelContextProtocol.Server.Tools;

public class WeatherServer
{
    public static async Task Main(string[] args)
    {
        // Create an MCP server
        var server = new McpServer(
            name: "Weather MCP Server",
            version: "1.0.0"
        );
        
        // Register our custom weather tool
        server.AddTool<string, WeatherData>("weatherTool", 
            description: "Gets current weather for a location",
            execute: async (location) => {
                // Call weather API (simplified)
                var weatherData = await GetWeatherDataAsync(location);
                return weatherData;
            });
        
        // Connect the server using stdio transport
        var transport = new StdioServerTransport();
        await server.ConnectAsync(transport);
        
        Console.WriteLine("Weather MCP Server started");
        
        // Keep the server running until process is terminated
        await Task.Delay(-1);
    }
    
    private static async Task<WeatherData> GetWeatherDataAsync(string location)
    {
        // This would normally call a weather API
        // Simplified for demonstration
        await Task.Delay(100); // Simulate API call
        return new WeatherData { 
            Temperature = 72.5,
            Conditions = "Sunny",
            Location = location
        };
    }
}

public class WeatherData
{
    public double Temperature { get; set; }
    public string Conditions { get; set; }
    public string Location { get; set; }
}
```

### Java Example: MCP Server Components

This example demonstrates the same MCP server and tool registration as the .NET example, but implemented in Java.

```java
import io.modelcontextprotocol.server.McpServer;
import io.modelcontextprotocol.server.McpToolDefinition;
import io.modelcontextprotocol.server.transport.StdioServerTransport;
import io.modelcontextprotocol.server.tool.ToolExecutionContext;
import io.modelcontextprotocol.server.tool.ToolResponse;

public class WeatherMcpServer {
    public static void main(String[] args) throws Exception {
        // Create an MCP server
        McpServer server = McpServer.builder()
            .name("Weather MCP Server")
            .version("1.0.0")
            .build();
            
        // Register a weather tool
        server.registerTool(McpToolDefinition.builder("weatherTool")
            .description("Gets current weather for a location")
            .parameter("location", String.class)
            .execute((ToolExecutionContext ctx) -> {
                String location = ctx.getParameter("location", String.class);
                
                // Get weather data (simplified)
                WeatherData data = getWeatherData(location);
                
                // Return formatted response
                return ToolResponse.content(
                    String.format("Temperature: %.1f°F, Conditions: %s, Location: %s", 
                    data.getTemperature(), 
                    data.getConditions(), 
                    data.getLocation())
                );
            })
            .build());
        
        // Connect the server using stdio transport
        try (StdioServerTransport transport = new StdioServerTransport()) {
            server.connect(transport);
            System.out.println("Weather MCP Server started");
            // Keep server running until process is terminated
            Thread.currentThread().join();
        }
    }
    
    private static WeatherData getWeatherData(String location) {
        // Implementation would call a weather API
        // Simplified for example purposes
        return new WeatherData(72.5, "Sunny", location);
    }
}

class WeatherData {
    private double temperature;
    private String conditions;
    private String location;
    
    public WeatherData(double temperature, String conditions, String location) {
        this.temperature = temperature;
        this.conditions = conditions;
        this.location = location;
    }
    
    public double getTemperature() {
        return temperature;
    }
    
    public String getConditions() {
        return conditions;
    }
    
    public String getLocation() {
        return location;
    }
}
```

### Python Example: Building an MCP Server

This example shows how to build an MCP server in Python, including two different methods for creating tools.

```python
#!/usr/bin/env python3
import asyncio
from mcp.server.fastmcp import FastMCP
from mcp.server.transports.stdio import serve_stdio

# Create a FastMCP server
mcp = FastMCP(
    name="Weather MCP Server",
    version="1.0.0"
)

@mcp.tool()
def get_weather(location: str) -> dict:
    """Gets current weather for a location."""
    # This would normally call a weather API
    # Simplified for demonstration
    return {
        "temperature": 72.5,
        "conditions": "Sunny",
        "location": location
    }

# Alternative approach using a class
class WeatherTools:
    @mcp.tool()
    def forecast(self, location: str, days: int = 1) -> dict:
        """Gets weather forecast for a location for the specified number of days."""
        # This would normally call a weather API forecast endpoint
        # Simplified for demonstration
        return {
            "location": location,
            "forecast": [
                {"day": i+1, "temperature": 70 + i, "conditions": "Partly Cloudy"}
                for i in range(days)
            ]
        }

# Initialize class for its methods to be registered as tools
weather_tools = WeatherTools()

if __name__ == "__main__":
    # Start the server with stdio transport
    print("Weather MCP Server starting...")
    asyncio.run(serve_stdio(mcp))
```

### JavaScript Example: Creating an MCP Server

This example demonstrates MCP server creation in JavaScript and how to register two weather-related tools.

```javascript
// Using the official Model Context Protocol SDK
import { McpServer } from "@modelcontextprotocol/sdk/server/mcp.js";
import { StdioServerTransport } from "@modelcontextprotocol/sdk/server/stdio.js";
import { z } from "zod"; // For parameter validation

// Create an MCP server
const server = new McpServer({
  name: "Weather MCP Server",
  version: "1.0.0"
});

// Define a weather tool
server.tool(
  "weatherTool",
  {
    location: z.string().describe("The location to get weather for")
  },
  async ({ location }) => {
    // This would normally call a weather API
    // Simplified for demonstration
    const weatherData = await getWeatherData(location);
    
    return {
      content: [
        { 
          type: "text", 
          text: `Temperature: ${weatherData.temperature}°F, Conditions: ${weatherData.conditions}, Location: ${weatherData.location}` 
        }
      ]
    };
  }
);

// Define a forecast tool
server.tool(
  "forecastTool",
  {
    location: z.string(),
    days: z.number().default(3).describe("Number of days for forecast")
  },
  async ({ location, days }) => {
    // This would normally call a weather API
    // Simplified for demonstration
    const forecast = await getForecastData(location, days);
    
    return {
      content: [
        { 
          type: "text", 
          text: `${days}-day forecast for ${location}: ${JSON.stringify(forecast)}` 
        }
      ]
    };
  }
);

// Helper functions
async function getWeatherData(location) {
  // Simulate API call
  return {
    temperature: 72.5,
    conditions: "Sunny",
    location: location
  };
}

async function getForecastData(location, days) {
  // Simulate API call
  return Array.from({ length: days }, (_, i) => ({
    day: i + 1,
    temperature: 70 + Math.floor(Math.random() * 10),
    conditions: i % 2 === 0 ? "Sunny" : "Partly Cloudy"
  }));
}

// Connect the server using stdio transport
const transport = new StdioServerTransport();
server.connect(transport).catch(console.error);

console.log("Weather MCP Server started");
```

This JavaScript example also shows how to create an MCP client that connects to a server, sends a prompt, and processes the response, including any tool calls made.

## Security and Authorization

MCP includes built-in concepts and mechanisms for managing security and authorization throughout the protocol:

1. **Tool Permission Control**:  
  Clients specify which tools a model can use during a session. This ensures only explicitly authorized tools are accessible, reducing the risk of unintended or unsafe operations. Permissions can be configured dynamically based on user preferences, organizational policies, or interaction context.

2. **Authentication**:  
  Servers may require authentication before granting access to tools, resources, or sensitive operations. This can involve API keys, OAuth tokens, or other methods. Proper authentication ensures only trusted clients and users can invoke server-side features.

3. **Validation**:  
  Parameter validation is enforced for all tool calls. Each tool defines expected types, formats, and constraints for its parameters, and the server validates incoming requests accordingly. This prevents malformed or malicious input from affecting tool operations and maintains integrity.

4. **Rate Limiting**:  
  To prevent abuse and ensure fair use of server resources, MCP servers can implement rate limits for tool calls and resource access. Limits may apply per user, session, or globally, protecting against denial-of-service attacks or excessive consumption.

Together, these mechanisms provide a secure foundation for integrating language models with external tools and data sources, while giving users and developers fine-grained control over access and usage.

## Protocol Messages

MCP communication uses structured JSON messages to ensure clear and reliable interactions between clients, servers, and models. The main message types include:

- **Client Request**  
  Sent from client to server, typically including:  
  - The user's prompt or command  
  - Conversation history for context  
  - Tool configuration and permissions  
  - Additional metadata or session info

- **Model Response**  
  Returned by the model (via client), containing:  
  - Generated text or completion based on prompt and context  
  - Optional tool call instructions if the model decides a tool should be invoked  
  - References to resources or additional context as needed

- **Tool Request**  
  Sent from client to server when a tool needs to be executed. This includes:  
  - The tool’s name  
  - Parameters required by the tool (validated against its schema)  
  - Contextual information or identifiers for tracking

- **Tool Response**  
  Returned by the server after tool execution, providing:  
  - Results of the tool (structured data or content)  
  - Any errors or status info if the tool call failed  
  - Optional metadata or logs related to the execution

These structured messages ensure each step in the MCP workflow is explicit, traceable, and extensible, supporting advanced scenarios like multi-turn conversations, tool chaining, and robust error handling.

## Key Takeaways

- MCP uses a client-server architecture to connect models with external capabilities.
- The ecosystem includes clients, hosts, servers, tools, and data sources.
- Communication can happen via STDIO, SSE, or WebSockets.
- Tools are the fundamental units of functionality exposed to models.
- Structured communication protocols ensure consistent interactions.

## Exercise

Design a simple MCP tool that would be useful in your domain. Define:  
1. The tool’s name  
2. The parameters it accepts  
3. The output it returns  
4. How a model might use this tool to solve user problems

---

## What's next

Next: [Chapter 2: Security](/02-Security/README.md)

**Disclaimer**:  
This document has been translated using the AI translation service [Co-op Translator](https://github.com/Azure/co-op-translator). While we strive for accuracy, please be aware that automated translations may contain errors or inaccuracies. The original document in its native language should be considered the authoritative source. For critical information, professional human translation is recommended. We are not liable for any misunderstandings or misinterpretations arising from the use of this translation.