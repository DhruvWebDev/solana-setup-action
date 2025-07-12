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

---

## 🚀 Quick Usage

```yaml
# .github/workflows/solana.yml
name: Solana CI

on: [push]

jobs:
  setup-solana:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Setup Solana Environment 🌞
        uses: DhruvWebDev/solana-setup-action@v0.0.7
        with:
          node-version: '18'
          solana-cli-version: '1.18.18'
          anchor-version: '0.30.1'
          pnpm-package-manager: '8.15.5'
          yarn-package-manager: '1.22.19'
          x-ray-enabled: true
          working-directory: ./path

      - name: Check Solana Installation
        run: |
          solana --version
          anchor --version
