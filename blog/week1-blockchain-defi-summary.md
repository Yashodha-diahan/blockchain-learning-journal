Week 1: What I Learned About Blockchain & DeFi
By Yashodha | DeFi Developer Roadmap - Week 1 Summary

I'm a software engineering student transitioning into blockchain development, specifically DeFi (Decentralized Finance). This is my Week 1 summary — everything I learned from scratch about how blockchain works, written in my own words so I actually understand it, not just memorize it.

What is Blockchain?
The simplest way I can explain blockchain: it's a shared notebook that thousands of computers hold copies of. When someone adds a new page (called a block), every computer copies it. If anyone tries to change an old page, everyone else's copies prove it was tampered with.
Each block contains three things:

A batch of transactions (like "Alice sent 5 ETH to Bob")
A hash — a unique fingerprint of all the data inside
The previous block's hash — this is what links them into a chain

This linking is what makes it secure. If someone changes Block #1, its hash changes, which breaks Block #2's reference, which breaks Block #3, and so on. You'd have to redo the entire chain — practically impossible.
The key properties I learned:

Decentralized — no single company or bank controls it
Immutable — once data is written, it can't be changed
Transparent — anyone can verify any transaction
Consensus — all nodes (computers) must agree on what's valid

Bitcoin was the first blockchain (2009) — it's basically digital money. But Ethereum (2015) is what matters for me as a developer because it supports smart contracts — programs that run on the blockchain.

What are Smart Contracts?
This was my favorite topic. A smart contract is self-executing code that lives on the blockchain. Think of it like a vending machine — you put in money (send a transaction), select what you want (call a function), and the machine automatically gives you the item (code executes). No shopkeeper needed.
Here's what makes them special:

Trustless — you don't need to trust anyone, the code enforces the rules
Immutable — once deployed, nobody can change it (not even the creator!)
Composable — contracts can call other contracts, like stacking LEGO blocks
Deterministic — same input always gives the same output

The scary part? Since they're immutable, bugs are permanent. In 2016, a bug in a smart contract called "The DAO" led to $60 million being stolen. That's why security is the most important skill I need to learn.
Smart contracts are written in Solidity (for Ethereum), and every DeFi protocol — Uniswap, Aave, Compound — is just a collection of smart contracts.

How Gas Works
This one confused me at first, but now I get it. Gas is the fee you pay for any action on Ethereum. Every computation costs gas because validators (the computers running Ethereum) need to be compensated for processing your transaction.
The formula is simple:

Transaction Fee = Gas Used × Gas Price


Gas Used = how much computation your transaction needs. A simple ETH transfer = 21,000 gas. A complex DeFi swap = 150,000+ gas.
Gas Price = measured in Gwei (1 Gwei = 0.000000001 ETH). This fluctuates based on network demand.
1 ETH = 1,000,000,000 Gwei (10^18 Wei)

Since the EIP-1559 upgrade, fees are split into:

Base fee — set by the network, gets burned (destroyed forever)
Priority fee (tip) — you set this, goes to the validator, higher tip = faster inclusion

The biggest takeaway for me as a developer: writing to the blockchain costs gas, but reading is free. So every line of Solidity code I write has a real cost for my users. If my code is inefficient, users pay more and will switch to a cheaper protocol. Gas optimization is an actual job skill.

How Wallets Work
A wallet is your identity on the blockchain. It doesn't actually "hold" your crypto — the blockchain holds it. The wallet holds your keys that prove you own it.
Three layers of identity:

Seed Phrase (12 or 24 words) — The master key. Generates everything else. Write it on paper ONLY. Never screenshot. Never store digitally. If someone gets this, they control all your wallets.
Private Key (256-bit number) — Generated from the seed phrase. Signs every transaction you make. MetaMask stores this encrypted on your device. NEVER share with anyone.
Public Address (starts with 0x, 42 characters) — Safe to share. This is where people send you crypto. Like an email address.

Two types of wallets:

Hot wallets (MetaMask, Trust Wallet) — connected to internet, convenient but less secure
Cold wallets (Ledger, Trezor) — offline hardware devices, most secure

I set up MetaMask this week, switched to the Sepolia testnet, got free test ETH from a faucet, and sent my first transaction. Seeing it confirmed on Etherscan and reading every field (tx hash, gas used, nonce, block number) connected everything I learned from Days 1-5.

What is DeFi?
DeFi stands for Decentralized Finance. It takes everything banks do and replaces the bank with smart contracts. No humans approving loans. No opening hours. No paperwork. Just code running 24/7, accessible to anyone with a wallet.
The 5 pillars I learned:

DEX (Swapping) — Trade tokens without a middleman. Uses AMM (Automated Market Maker) with the formula x × y = k. Example: Uniswap.
Lending — Deposit crypto to earn interest, or borrow by putting up collateral. Everything is over-collateralized (deposit $150 to borrow $100). If your collateral drops, you get liquidated. Example: Aave, Compound.
Staking — Lock your tokens in a contract to earn rewards over time. Example: Lido.
Stablecoins — Tokens pegged to $1 so you can avoid volatility. USDC is backed by real dollars, DAI is backed by ETH collateral. Essential for DeFi to function.
Yield / Vaults — Automated strategies that compound your returns. Deposit once, the vault does the rest. Example: Yearn Finance.

The most powerful concept is composability — since contracts can call other contracts, you can chain them together. Borrow from Aave → swap on Uniswap → stake on Lido → all in one transaction. This is called "money legos" and it's what makes DeFi so revolutionary compared to traditional banking.
