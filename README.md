# 🚀 Woxchain Testnet Node Setup Guide

This guide will help you run a **Woxchain Testnet Node** using the official client.  
Woxchain is a high-performance Proof-of-Authority (PoA) blockchain focused on scalability, speed, and EVM compatibility.

---

## 🌐 Network Details

| Key                | Value                            |
|--------------------|----------------------------------|
| Network Name       | Woxchain Testnet                 |
| RPC URL            | https://rpctest.woxchain.com     |
| Chain ID           | 893758                           |
| Currency Symbol    | WOX                              |
| Block Explorer     | [testnet.woxscan.com](https://testnet.woxscan.com) |

---

## 📦 Requirements

- OS: Ubuntu 20.04 or later (Debian tabanlı sistemler önerilir)
- CPU: 2+ cores
- RAM: 4+ GB
- Disk: 50+ GB SSD
- Geth version (modified for Woxchain)
- Docker (optional but supported)

---

## 🔧 1. Installation (Manual)

### Clone the Repository

```bash
git clone https://github.com/woxchain/woxchain-node.git
cd woxchain-node
```

### Build the Node

```bash
chmod +x ./scripts/build.sh
./scripts/build.sh
```

### Initialize the Chain

```bash
./woxchaind init "Wox Test Node" --chain-id 893758
cp config/genesis.json ~/.woxchaind/config/
./woxchaind genesis import ~/.woxchaind/config/genesis.json
```

### Start the Node

```bash
./woxchaind start   --http   --http.addr 0.0.0.0   --http.port 8545   --http.api "eth,net,web3"   --networkid 893758
```

---

## 🐳 2. Installation (Docker Method)

If you prefer Docker:

```bash
git clone https://github.com/woxchain/woxchain-node.git
cd woxchain-node/docker
docker compose up -d
```

Optional: Modify `docker-compose.yml` for ports or custom config.

---

## ✅ 3. Check Node Status

Use cURL or Postman to verify your node is live:

```bash
curl -X POST https://<YOUR-IP>:8545   -H "Content-Type: application/json"   -d '{"jsonrpc":"2.0","method":"eth_blockNumber","params":[],"id":1}'
```

---

## 🛠 Tips & Maintenance

- Keep your node synced with peers (check logs for sync status)
- Restart your node periodically for updates
- Check logs: `tail -f ~/.woxchaind/logs/woxchain.log`
- Use Nginx + Certbot if you want to serve RPC over HTTPS

---

## 🔐 Validator Mode (Optional)

If you're whitelisted as a validator:

```bash
./woxchaind --mine --miner.threads=1 --unlock <your-address> --password password.txt
```

Use a secure keystore and avoid exposing the private key.

---

## 🧪 Test Your Node

- Deploy contracts using Remix or Hardhat
- Monitor using [testnet.woxscan.com](https://testnet.woxscan.com)
- Request test tokens from faucet (coming soon)

---

## 📚 Resources

- [Explorer](https://testnet.woxscan.com)
- [Faucet](https://faucet.woxchain.com)
- [GitHub](https://github.com/woxchain)
- [Telegram](https://t.me/woxchain)

---

## ❓ Troubleshooting

| Problem | Solution |
|--------|----------|
| Node stuck syncing | Ensure correct genesis file and peers |
| RPC not responding | Open port 8545 on your firewall |
| Chain ID mismatch | Double-check you're using `893758` |

---

**Woxchain Testnet — Building the Future of Decentralized Infrastructure.**
