# StellarAjo

  Bringing Africa's most trusted savings tradition on-chain.
StellarSusu is an open-source organisation building the mobile-first frontend layer for the Soroban smart contract on the Stellar network that eliminates the single biggest risk in traditional rotating savings: trusting a human collector with everyone's money.

---

## The Problem We Solve

**Susu. Ajo. Chama. Stokvel. Tontine. Adashi. Upatu.**
These are the same idea, spoken in dozens of languages across Africa and its diaspora. A group of trusted people pool a fixed contribution every cycle, and each member takes the full pot in turn. It is the primary savings mechanism for hundreds of millions of people — in Ghana alone, up to 95% of adults participate.
The system works on social trust. And that is also its fatal flaw.
When a collector absconds with the funds, participants have no contract, no receipts, and no legal recourse. The SoroSusu-Protocol eliminates this entirely by encoding the rules of a Susu group directly into a Soroban smart contract: contributions are locked, disbursement is automatic, and no single person can redirect the funds.

**The contract is live. The trust layer is built. StellarSusu builds the experience that makes it invisible.**

---

## Our Mission

Make blockchain-secured Susu feel as simple and familiar as a WhatsApp group — for a market trader in Accra, a nurse in Nairobi, a diaspora community in London, and a Stokvel in Johannesburg.

---

## Repositories

| Repo | Description |
|---|---|
| [`stellarsusu-app`](./stellarsusu-app) | React Native mobile app (iOS & Android) |
| [`stellarsusu-protocol`](https://github.com/sorosusu/SoroSusu-Protocol) | Soroban smart contract (upstream, shared org) |
| [`stellarsusu-sdk`](./stellarsusu-sdk) | TypeScript SDK wrapping contract interactions |
| [`stellarsusu-docs`](./stellarsusu-docs) | User guides, API references, and integration docs |

---

## Architecture Overview

```
┌─────────────────────────────────────────────────┐
│              StellarSusu Mobile App              │
│             (React Native · Expo)                │
│                                                  │
│  ┌──────────────┐      ┌──────────────────────┐  │
│  │  Group UI    │      │  Wallet & Identity   │  │
│  │  Ajo · Chama │      │  Freighter · LOBSTR  │  │
│  │  Susu · Etc. │      │  Passkeys            │  │
│  └──────┬───────┘      └──────────┬───────────┘  │
│         └──────────┬──────────────┘              │
│                    ▼                              │
│         ┌──────────────────┐                     │
│         │  StellarSusu SDK │                     │
│         │  (TypeScript)    │                     │
│         └────────┬─────────┘                     │
└──────────────────┼──────────────────────────────┘
                   ▼
     ┌─────────────────────────┐
     │   SoroSusu-Protocol     │
     │   Soroban Smart Contract│
     │   (Stellar Network)     │
     └─────────────────────────┘
```

---

## Key Features

### For Group Members
- 🫱🏾‍🫲🏽 **Create or join a Susu group** with a shareable link or QR code
- 📅 **Contribution reminders** with local currency display
- 🔔 **Real-time notifications** when your payout cycle arrives
- 🌐 **Multilingual UI** — English, Français, Twi, Yoruba, Swahili, Zulu (expanding)

### For Group Organisers
- ⚙️ **Configurable group rules** — contribution amount, cycle length, member count, payout order
- 🗳️ **On-chain consensus** for adding or removing members
- 📊 **Transparency dashboard** — every contribution and disbursement is visible to all members

### Trust & Security
- 🔒 **Non-custodial** — the smart contract holds funds, not StellarSusu
- ✅ **Automatic disbursement** — no human approval required for payouts
- 🧾 **Immutable receipts** — every transaction permanently recorded on Stellar
- 🚨 **Penalty enforcement** — late contributions handled by contract logic, not social pressure

---

## Tech Stack

| Layer | Technology |
|---|---|
| Mobile App | React Native + Expo |
| Styling | NativeWind (Tailwind for RN) |
| State Management | Zustand + React Query |
| Blockchain | Stellar Soroban · `@stellar/stellar-sdk` |
| Wallet Integration | Freighter · WalletConnect · Passkeys |
| Backend (optional) | Supabase (notifications, contacts sync) |
| Contract Language | Rust (Soroban) — upstream |

---

## Getting Started

### Prerequisites

- Node.js 18+
- Expo CLI (`npm install -g expo-cli`)
- A Stellar testnet wallet (Freighter extension or Lobstr mobile)

### Installation

```bash
# Clone the app
git clone https://github.com/stellarsusu/stellarsusu-app.git
cd stellarsusu-app

# Install dependencies
npm install

# Copy environment config
cp .env.example .env
# Add your Stellar RPC URL and network passphrase

# Start on testnet
npm run start
```

### Run on Device

```bash
# iOS
npm run ios

# Android
npm run android
```

See [`stellarsusu-app/README.md`](./stellarsusu-app/README.md) for full setup instructions, including wallet pairing and testnet faucet access.

---

## Contract Integration

StellarSusu is built directly on top of the [SoroSusu-Protocol](https://github.com/sorosusu/SoroSusu-Protocol). The core contract functions our app invokes are:

| Function | Description |
|---|---|
| `create_group` | Initialises a new Susu group with configured parameters |
| `join_group` | Adds a member to an existing group |
| `contribute` | Locks a member's contribution for the current cycle |
| `disburse` | Releases the pot to the current cycle's recipient |
| `get_group_state` | Reads full group status — members, balances, cycle |
| `leave_group` | Exits a group (subject to penalty rules) |

Full contract ABI and event schema: [`stellarsusu-docs/contract-reference.md`](./stellarsusu-docs/contract-reference.md)




