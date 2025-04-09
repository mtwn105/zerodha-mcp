# Zerodha MCP Server & Client

A Python-based trading assistant that connects to a Zerodha MCP server to help users manage their trading account.

## Features

- **Account Management**: Manage Zerodha trading account, orders, and positions
- **Interactive Chat Interface**: Natural language interface for trading operations
- **MCP Integration**: Built on the Model Context Protocol for standardized communication
- **Zerodha API Integration**: Uses Zerodha's API to interact with the trading platform
- **Agno Agent**: Uses Agno Agent to interact with the trading platform

## Tech Stack

- **Protocol**: [Model Context Protocol (MCP)](https://modelcontextprotocol.io/)
- **Agent Framework**: [Agno](https://github.com/agno-agi/agno)

## Tools

- **Place Orders**: Place orders in the trading platform
- **Modify Orders**: Modify orders in the trading platform
- **Cancel Orders**: Cancel orders in the trading platform
- **Get Orders**: Get orders in the trading platform
- **Get Order History**: Get order history in the trading platform
- **Get Order Trades**: Get order trades in the trading platform
- **Get Margins**: Get margins in the trading platform
- **Get Holdings**: Get holdings in the trading platform
- **Get Positions**: Get positions in the trading platform
- **Get User Profile**: Get user profile in the trading platform

## Prerequisites

- Python
- Zerodha trading account with Personal API access from [here](https://developers.kite.trade/login)
- Zerodha API key and secret
- OpenAI API key (for Agno Agent)

## Installation

1. Clone the repository:

```bash
git clone https://github.com/yourusername/zerodha-mcp-server-client.git
cd zerodha-mcp-server-client
```

2. Create and activate a virtual environment:

```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install dependencies:

```bash
pip install -r requirements.txt
```

4. Create a `.env` file with your configuration:

```env
# Server Configuration
ZERODHA_API_KEY=your_api_key
ZERODHA_API_SECRET=your_api_secret
PORT=8001
SERVER_MODE=sse  # or stdio

# Client Configuration
MCP_HOST=localhost
MCP_PORT=8001
OPENAI_API_KEY=your_openai_api_key
```

## Server Usage

The server provides a set of tools for interacting with the Zerodha trading platform. To start the server:

1. Make sure your `.env` file is properly configured with your Zerodha API credentials.

2. Start the server using one of the following methods:

```bash
# Using environment variables
python server.py

# Or using command line arguments
python server.py --api-key your_api_key --api-secret your_api_secret --port 8001 --mode sse
```

The server provides the following tools:

- `get_login_url`: Get the login URL for user authentication
- `get_access_token`: Generate access token using request token
- `get_user_profile`: Get user's Zerodha profile information
- `get_margins`: Get available margins and fund details
- `get_holdings`: Get portfolio holdings
- `get_positions`: Get current positions
- `get_orders`: Get all orders for the day
- `get_order_history`: Get history of a specific order
- `get_order_trades`: Get trades generated by an order
- `place_order`: Place a new order
- `modify_order`: Modify an existing order
- `cancel_order`: Cancel an order

## Client Usage

The client connects to the MCP server and provides an interactive interface for trading operations.

1. Start the client using one of the following methods:

```bash
# Using environment variables from .env file
python client.py

# Using command line arguments
python client.py --host localhost --port 8001

# Using a combination (command line arguments take precedence)
MCP_HOST=localhost MCP_PORT=8001 python client.py --host otherhost --port 9000
```

The client supports configuration through multiple sources, with the following precedence:

1. Command-line arguments (highest precedence)
2. Environment variables
3. `.env` file
4. Default values (lowest precedence)

Configuration options:

- Environment variables: `MCP_HOST` and `MCP_PORT`
- Command-line arguments: `--host` and `--port`
- `.env` file variables: `MCP_HOST` and `MCP_PORT`

Default values (if no configuration is provided):

- Host: localhost
- Port: 8001

The client automatically loads environment variables from the `.env` file in the project root directory. Make sure your `.env` file contains the necessary configuration:

```env
# Client Configuration
MCP_HOST=localhost
MCP_PORT=8001
```

2. The client will automatically connect to the MCP server using the provided configuration.

3. Once connected, you can interact with the assistant using natural language commands. For example:

   - "Show me my portfolio holdings"
   - "What are my current positions?"
   - "Place a market order for 10 shares of RELIANCE"
   - "Cancel order ID 123456"

4. To exit the client, type 'quit' when prompted.

## Development

### Project Structure

- `client.py`: MCP client implementation with interactive chat interface
- `server.py`: MCP server implementation with Zerodha API integration
- `generate_token.py`: Utility for generating access tokens
- `requirements.txt`: Project dependencies
- `.env`: Environment configuration

### Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Built using [Agno](https://github.com/agno-agi/agno)
- Uses [MCP](https://modelcontextprotocol.io/) for standardized communication
- Powered by [KiteConnect](https://kite.trade/) for Zerodha API integration
