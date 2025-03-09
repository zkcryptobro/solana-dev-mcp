# Solana Model Context Protocol (MCP) Demo

This repository demonstrates a simple implementation of a Model Context Protocol (MCP) server for Solana development.

## What is MCP?

The Model Context Protocol (MCP) is a standardized interface for AI models to interact with tools and resources. This demo showcases a simple MCP server implementation that provides:

1. Basic RPC methods for Solana (getBalance, getAccountInfo, getTransaction)
2. Some helpful prompts for Solana development

## Prerequisites

- Node.js (v16 or higher recommended)
- pnpm package manager (v9.10.0 or compatible)

## Installation

Clone this repository and install dependencies:

```bash
git clone https://github.com/yourusername/solana-dev-mcp.git
cd solana-dev-mcp
pnpm install
```

## Testing Your Installation

To verify that everything is working correctly, run the following command:

```bash
pnpm run check-install
```

This command will:

1. Compile the TypeScript code to JavaScript
2. Start the MCP server
3. Send test messages to the server
4. Verify that the server responds correctly

If all tests pass, you'll see a success message confirming that your installation is working correctly.

## Getting Started

1. **Explore the code**: The main implementation is in `index.ts`, which sets up an MCP server with simple fetching tools and a docs resources.

2. **Modify the server**: You can extend the server by adding more tools and resources based on your needs.

3. **Integrate with Solana**: This basic implementation can be extended to interact with Solana blockchain by adding tools for wallet operations, transaction signing, etc.

## Example Usage

Add this to your Claude desktop config by doing so:

```json
{
  "mcpServers": {
    "solana-dev": {
      "command": "pnpm",
      "args": ["ts-node", "<full-path-to-repo>/index.ts"]
    }
  }
}
```

## Project Structure

- `index.ts` - Main server implementation
- `package.json` - Project dependencies and metadata
- `tsconfig.json` - TypeScript configuration

## Ideas Extending MCP for Solana Development

This MCP server implementation provides a foundation that you can extend or fork for your own Solana development needs. Here are some ideas to get you started:

### Ideas for Extension

1. **Priority Fee Estimator**: Add a tool that estimates optimal priority fees for Solana transactions based on recent network activity. This could help users optimize transaction costs while ensuring timely processing.

2. **Solana Verify Debugger**: Create a tool that helps debug issues with `solana-verify` by providing more detailed information about the verification process.

3. **Solana Security.txt Inspector**: Build a tool that extracts and displays the security.txt file information for a given Solana program, making it easier to contact the program's maintainers with security concerns.

4. **Squads Helper for Program Deployment**: Create a tool that automates the process of deploying and upgrading Solana programs, making it easier to manage program state across multiple environments.

5. **Anchor-Error Explainer**: Develop a tool that takes an error code and looks up the corresponding human-readable error message from the Anchor error code database.

6. **Enhanced Prompts**: Expand the server's prompt capabilities to provide more context-aware suggestions for Solana development tasks. For example, add prompts for common transaction patterns, account creation, or token operations.

7. **Transaction Builder**: Create tools that help construct complex transactions with multiple instructions, making it easier to interact with various Solana programs.

8. **Custom RPC Endpoints**: Allow configuration of custom RPC endpoints, including support for private RPC providers or local validators.

9. **Program Deployment Helpers**: Create tools that simplify the process of deploying and upgrading Solana programs.

10. **Account & Transaction Explorer**: Add a tool that takes an account or transaction ID and displays the contents in a human-readable format, similar to an explorer view. This could be useful for inspecting transaction data or account state without needing to manually decode the data.

### How to Contribute

If you've built an extension that might be useful to others, consider submitting a pull request to this repository. Make sure to follow these guidelines:

1. Keep your code well-documented
2. Include tests for new functionality
3. Follow the existing code style
4. Update the README with information about your addition

## License

ISC
