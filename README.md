# Privy Solana MCP Demo

This repository demonstrates using a Model Context Protocol (MCP) server to allow users to interface with Privy wallets on Solana via natural language. It is a fork of the [original MCP Demo](https://github.com/solana-foundation/solana-dev-mcp) implemented by the Solana Foundation and adds a `transferSOL` function to allows users to transfer SOL via natural language.

## 0. Prerequisites

- Node.js (v16 or higher recommended)
- pnpm package manager (v9.10.0 or compatible)
- Claude Desktop (download [here](https://claude.ai/download))

## 1. Installation

Clone this repository and install dependencies:

```bash
git clone https://github.com/privy-io/solana-dev-mcp.git
cd solana-dev-mcp
pnpm install
```

## 2. Set your environment variables

Create an `.env` file from a copy of the provided `.env.example` file:

```bash
cp .env.example .env
```

In your `.env` file, add values for all of the provided environment variables:

```
PRIVY_APP_ID=<your-privy-app-id>
PRIVY_APP_SECRET=<your-privy-app-secret>

PRIVY_WALLET_ID=<your-privy-wallet-id>
PRIVY_WALLET_ADDRESS=<your-privy-wallet-address>

SOLANA_CLUSTER_URL=<your-solana-rpc-url>
SOLANA_CLUSTER_NAME=<your-solana-cluster> # defaults to mainnet-beta
```

This ensures that your MCP server can only control your wallet and is able to make transaction requests to the Solana blockchain.

## 3. Run the server

Run the server with the following command:
```bash
npx @modelcontextprotocol/inspector ts-node index.ts
```

If you open the URL printed to the console, you can access an MCP inspector that allows you to test the functionality of tools and resources directly, allowing for a faster iteration cycle.

In the next step, we'll connect this running server to Claude to allow you to control your wallet via natural language.

## 4. Set your Claude Desktop configuration

To connect your Claude Desktop app to your MCP server, you must set a Claude MCP configuration file [like so](https://modelcontextprotocol.io/quickstart/user). 

In particular, create a new JSON configuration file at `~/Users/<your-username>/Library/Application Support/Claude/claude_desktop_config.json` if one does not already exist yet. Then in the file, paste the following contents:

```json
{
  "mcpServers": {
    // You may rename the name of your MCP server.
    "privy-solana-mcp": {
      "command": "ts-node",
      "args": ["/<absolute-path-to-your-mcp-server-repo>/index.ts"],
      "env": {
        "PRIVY_APP_ID": "your-privy-app-id",
        "PRIVY_WALLET_ID": "your-privy-wallet-id",
        "PRIVY_WALLET_ADDRESS": "your-privy-wallet-address",
        "PRIVY_APP_SECRET": "your-privy-app-secret",
        "SOLANA_CLUSTER_URL": "your-solana-rpc-url",
        "SOLANA_CLUSTER_NAME": "your-solana-cluster"
      }
    }
    // Feel free to include other MCP servers here
  }
}
```

Claude Desktop cannot access environment variables from your MCP server, so they must be replicated in the Claude configuration file.

## 5. Try it out!

Now, once you've set your Claude configuration file and have your MCP server running, open Claude desktop. 

You can now ask Claude to perform queries or actions on the Solana blockchain. For example, you might ask "What is my Solana wallet balance?" or "Can you transfer 0.005 SOL to <insert-address>?".

This section explains how to use the Solana MCP server in [Claude](https://modelcontextprotocol.io/quickstart/user).
Follow the same steps to use the Solana MCP server in [Windsurf](https://docs.codeium.com/windsurf/mcp) and [Cursor](https://docs.cursor.com/context/model-context-protocol).

# Security

This is a simple example and should not be used in production. MCP is a new standard, and lacks proper security measures. In particular, there is no accepted standard for how end users should authenticate with MCP servers, which is critical to ensuring that end users can only take actions with wallets they control. 

Please be extremely careful when installing & trying out MCP servers from unknown developers.

Please use a sandboxed environment when trying out MCP servers, with no crucial information in it to prevent potential damage.
