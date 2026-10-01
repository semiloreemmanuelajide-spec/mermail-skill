# Autonomous Email-to-Swap Trading Agent

A reusable Mermail Agent Skill that monitors an agent's Mermail inbox for incoming token signal emails, executes an automated token swap on Solana using the Mermail Agent Wallet, and replies to the sender with the transaction hash.

## What It Enables
- **Web2-to-Web3 Automation:** Bridges traditional email notifications directly with automated on-chain crypto transactions.
- **Hands-Free Trading:** Eliminates manual copying of contract addresses from email alerts into decentralized exchange UIs.
- **Verification Loop:** Automatically sends an email confirmation back to the sender with on-chain proof of execution.

## How It Interacts with Mermail
- **Mermail Inbox:** Uses `list_emails` and `get_email` to read incoming signal messages, and `send_email` to reply with transaction receipts.
- **Agent Wallet:** Uses Mermail's wallet tools to sign and execute SOL-to-token swaps on Solana.

## Workflow
1. **Fetch Signal:** The agent queries the Mermail inbox for unread messages containing token contract addresses.
2. **Parse Payload:** The agent extracts the Solana token contract address (CA) from the email body.
3. **Execute Swap:** The agent invokes the Agent Wallet tool to swap SOL (e.g., 0.005 SOL) for the specified token.
4. **Send Receipt:** The agent replies to the original email thread with the transaction hash and a confirmation message.

## Example Prompts & Expected Results

### Example Prompt
> "Check my Mermail inbox for an unread email containing a Solana token address. Buy 0.005 SOL worth of that token using the Agent Wallet, and reply to the sender with the transaction hash."

### Expected Result
- **Input Email:** Body containing a valid Solana contract address (e.g., `DezXAZ8z7PnrnRJjz3wXBoRgixCa6xjnB7YaB1pPB24`).
- **Agent Action:** Reads the message, parses the address, and executes a 0.005 SOL swap via the Agent Wallet.
- **Output Reply:** Email sent back to the original sender stating:
  > "Successfully purchased token `DezXAZ8z7PnrnRJjz3wXBoRgixCa6xjnB7YaB1pPB24` for 0.005 SOL. Transaction hash: ``."