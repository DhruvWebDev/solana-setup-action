# 🧰 Solana Setup Action

> **Reusable GitHub Action to set up a complete Solana development environment**  
> Supports Solana CLI, Anchor, Node.js, and your favorite JS package managers (pnpm, yarn)!

---

## 📦 Features

✅ Installs **Node.js** (version of your choice)  
✅ Installs **Solana CLI** (official releases from [anza.xyz](https://release.anza.xyz))  
✅ Installs **Anchor CLI**  
✅ Installs **pnpm** and **Yarn** if needed  
✅ Setup **x-ray**(static analysis) to identify vulnerability in the contract
✅ Works in all Linux-based GitHub runners
✅ Build, Test and Deploy script feature

---

## 🚀 Quick Usage

```yaml
# .github/workflows/solana.yml
name:  CI
on:
  pull_request:
    branches: [ "main" ]
  push:
    branches: [ "main" ]

jobs:
  build-and-test-program:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4
      
      - name: Setup Solana Environment
        uses: DhruvWebDev/solana-setup-action@v0.1.8
        with:
          node-version: '20'
          solana-cli-version: '1.18.26'
          anchor-version: 'v0.31.1'
          solana-network-url: 'http://localhost:8899'
          solana-airdrop-amount: '100'
          solana-wallet-setup: true
          build-script: 'anchor build'
          # Add --skip-local-validator else the build would fail and another tip is to add --skip-build flag to fasten up the workflow because we have already built it in the anchor build
          test-script: 'anchor test  --skip-local-validator --skip-build'
          deploy-script: 'anchor deploy --skip-local-validator --skip-build'
          x-ray-enabled: true
          working-directory: './dir'
```
