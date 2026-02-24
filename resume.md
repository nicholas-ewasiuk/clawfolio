# Nick Ewasiuk — Full Stack Developer

## Overview

Full Stack Developer with 4 years of professional experience building across the Solana blockchain ecosystem. Transitioned from mechanical engineering through self-taught development into a full stack role at Step Finance, progressing from frontend protocol integrations to backend API architecture to Rust data pipelines. ~1,500 commits across 6 production repositories.

## Professional Experience

### Step Finance (Apr 2022 – Feb 2026)

Step Finance is the leading portfolio dashboard and DeFi data aggregator on Solana, serving 300K+ monthly active users. The platform aggregates wallet positions, transaction histories, and asset values across 40+ DeFi protocols into a single dashboard. Step also offered a commercial Portfolio Data API serving Tier 1 exchanges and institutions.

#### Role Progression

- **Frontend Team (Apr 2022 – Nov 2024)**: Built DeFi protocol integrations for the React/TypeScript portfolio dashboard
- **Backend Team (Nov 2024 – Feb 2026)**: Built API services, data fetchers, Rust parsers, and the Remora trading platform

---

## Technical Skills

### Languages
- **TypeScript** — Primary language, 4 years production use across frontend and backend
- **Rust** — Transaction parsers, async data pipelines, Anchor smart contracts
- **HTML/CSS** — Frontend development, responsive UI
- **SQL** — PostgreSQL queries, Prisma ORM, ClickHouse analytics queries

### Frontend
- **React 18** — Hooks, context API, code splitting, lazy loading
- **React Query (TanStack)** — Server state management, cache invalidation, optimistic updates
- **Zustand** — Client state management
- **Ant Design** — UI component library
- **Emotion** — CSS-in-JS styling
- **ECharts** — Data visualization and charting
- **React Router v6** — Client-side routing

### Backend (Node.js)
- **NestJS 10/11** — Modular microservice architecture, guards, decorators, interceptors
- **Fastify** — High-performance HTTP server
- **Prisma** — Type-safe ORM with PostgreSQL
- **BullMQ** — Redis-backed job queues with scheduled/repeatable jobs
- **RabbitMQ (amqplib)** — Message queue consumers/producers, topic exchanges, dead-letter queues
- **JWT / Passport.js** — Authentication with custom Solana signature verification strategy
- **Swagger/OpenAPI** — API documentation generation

### Backend (Rust)
- **Tokio** — Async runtime, multi-threaded executor
- **Borsh / bincode** — Binary serialization/deserialization for Solana account data
- **Anchor** — IDL parsing, program interaction, code generation
- **lapin** — RabbitMQ client for Rust
- **ClickHouse client** — Batch insertion, analytics queries
- **proc-macro2 / syn** — Procedural macros for code generation
- **enum_dispatch** — Zero-cost type erasure for parser dispatch
- **rust_decimal / fixed** — Precise financial arithmetic
- **Serde** — Serialization framework

### Databases & Data Stores
- **PostgreSQL** — Relational data, double-entry ledger, referrals, user data
- **ClickHouse** — OLAP analytics, time-series data, OHLCV, mint prices
- **Redis** — Multi-tier caching, rate limiting, job queue persistence, distributed locks

### Solana / Web3
- **@solana/web3.js** — RPC calls, transaction construction, account deserialization
- **@coral-xyz/anchor** — Program interactions, IDL-based type generation
- **@solana/spl-token** — SPL token operations, Token-2022
- **Solana Wallet Adapter** — Multi-wallet connection (Phantom, Solflare, etc.)
- **Metaplex** — NFT metadata, compressed NFTs (cNFTs), bubblegum
- **Geyser Plugin** — Real-time transaction streaming from validators
- **Solana Snapshot ETL** — Historical state backfill from ledger snapshots
- **Squads Multisig** — On-chain multisig proposals and execution
- **Helius SDK** — RPC services, webhooks, DAS API for compressed NFTs

### Infrastructure & DevOps
- **Docker / Docker Compose** — Containerized deployments, multi-stage builds
- **CircleCI** — CI/CD pipelines (lint, type-check, test, build, deploy)
- **AWS** — ECR (container registry), ECS (container orchestration)
- **Prometheus** — Metrics collection and monitoring
- **Sentry** — Error tracking and reporting

### API Integrations (External)
- **Jupiter** — DEX aggregation, swap routing, limit orders, DCA, governance
- **OKX** — Centralized exchange swap quotes
- **Titan** — DEX swap aggregation
- **Alpaca** — Stock brokerage (buy/sell, positions, market data, corporate actions)
- **CoinGecko** — Exchange rates, token pricing
- **Magic Eden** — NFT marketplace data, collection pricing
- **Airtable** — CMS backend
- **SendGrid** — Email delivery
- **Arweave** — Decentralized storage (reward option claims data)

---

## Project Details

### 1. Step Frontend (488 commits)

React/TypeScript portfolio dashboard aggregating 40+ Solana DeFi protocols.

**DeFi Protocol Integrations Built:**
- **AMM/LP**: Orca (Whirlpools, double-dip), Raydium, Meteora, Saber, Atrix, Aldrin, Saros, Quarry, Sunny
- **Lending**: Tulip, Apricot, Francium, Solend, Sharky (NFT lending)
- **Staking**: Star Atlas (POLIS/ATLAS), UXD, Fabric, Marinade, Kamino
- **Perpetuals/Options**: Entropy, Zeta, Katana, Friktion (volts)
- **NFT**: Compressed NFT support (cNFT parsing, querying, send/burn), NFT gallery, floor pricing, staking

**Key Features:**
- Dashboard V3 refactor — migrated wallet data fetching to backend
- 15+ React contexts managing domain state (lending, staking, farms, margin, NFTs, etc.)
- Anchor program interactions for on-chain transactions (swaps, staking, LP management)
- Multi-language support (i18n)
- Solana wallet adapter integration

### 2. Step API Gateway (330 commits)

NestJS/Fastify API gateway — the main entry point for the Step ecosystem.

**Modules Built:**
- Portfolio aggregation (`/portfolio/all/:address`)
- Transaction history with CSV export and tax reporting
- Multi-DEX swap quotes (Jupiter, OKX, Titan)
- Solana Actions/Blinks integration for yield opportunities
- Reward options and contracts
- Oracle price endpoints
- Charts and analytics (ClickHouse-backed)
- Referrals system (v1 and v2)
- Profile management

**Step Portfolio API (Commercial Product):**
- API key lifecycle management (create, revoke, rotate)
- Credit-based billing with tiered pricing (Starter: 10K credits/19 USDC, Team: 3M credits/299 USDC)
- Usage statistics and tracking
- Developer documentation and onboarding
- Targeted at Tier 1 exchanges and institutions for SEC SAB 121 compliance
- Rate limiting per endpoint, JWT authentication

**Infrastructure:**
- JWT auth with Solana signature verification
- Role-based access control
- Multi-tier Redis caching with configurable stale times
- Prometheus metrics (migrated from CloudWatch)
- Swagger/OpenAPI documentation

### 3. Step Fetchers (328 commits)

48 RabbitMQ-driven data fetcher queues aggregating real-time Solana wallet positions.

**Fetcher Categories & Protocols:**
- **AMM (5)**: Raydium, Orca, Meteora standard, Saber, Saros, Marinade
- **CLMM (3)**: Raydium CLMM, Orca Whirlpools, Meteora DLMM
- **DEX (4)**: Jupiter, OpenBook v1/v2, Star Atlas
- **Farming (4)**: Raydium, Atrix, Quarry, Meteora
- **Lending (10)**: Kamino, MarginFi, Sharky, Francium, Save/Solend, Lulo, NX, DefiTuna, Loopscale, Jupiter
- **Margin/Perps (6)**: Drift, Parcl, Zeta, Jupiter, Flash Trade, Adrena
- **Staking (15)**: Raydium, Star Atlas, Bonfida, Bonk, Hubble, Drift, UXD, Jupiter, Kamino, HXRO, Realms, Pyth, Flash Trade, NX, Huma
- **Vaults (6)**: Kamino, Drift, Elemental, HawkFi, Allbridge, Loopscale
- **NFT (4)**: Compressed NFTs (DAS), Standard NFTs, Tensor, HadeSwap
- **Other**: Token balances, validators, domains (Bonfida, All Domains)

**Architecture:**
- RabbitMQ consumer with child process workers
- Multi-tier caching: Redis + in-memory (node-cache) with distributed locks
- Prometheus metrics endpoint
- Configurable timeout, retry logic, TTLs
- Parallel async execution with p-limit concurrency control
- BigNumber.js / Decimal.js for precise financial math

### 4. Step API Services (158 commits)

NestJS microservices with BullMQ job scheduling.

**Services:**
- Markets service — price aggregation from ClickHouse + CoinGecko exchange rates (runs every minute)
- Staking stats — APY calculations for Jito, Step validator, TheVault (runs every hour)
- Integrations — vault data loading, farm data, lending rates
- Reward options — on-chain call option indexing from Anchor programs + Arweave claims
- Bull Board — web UI for job queue monitoring

### 5. Step Ingestooor (47 commits)

Rust real-time blockchain data ingestion pipeline.

**Architecture:**
- Solana Geyser plugin → RabbitMQ → Parser Manager → ClickHouse
- 58 transaction parsers across 30+ protocols
- 43 distinct data types ("Dooots") — token balances, swaps, LP events, lending, staking, order book fills, etc.

**Parsers Built:**
- Raydium farms (v3, v5, v6)
- Meteora farms
- Jupiter

**Technical Details:**
- Async Tokio runtime with multi-threaded executor
- proc-macro code generation for parser and Dooot definitions
- Borsh / bincode deserialization of on-chain data
- Anchor IDL parsing for program instruction decoding
- Batch ClickHouse insertion with configurable flush intervals
- Dead-letter queues for error handling
- Prometheus metrics exposure via Axum HTTP server
- enum_dispatch for zero-overhead parser routing

### 6. Remora Backend (130 commits)

NestJS backend for a tokenized equities and crypto trading platform.

**Features Built:**
- Stock buy/sell endpoints with Alpaca brokerage integration
- Token mint/burn via Solana Squads multisig
- Double-entry ledger system (Prisma/PostgreSQL)
- Fiat-to-stablecoin conversion flow
- Transaction lifecycle management with atomic reversals
- Idempotency guards and race condition prevention
- Helius webhook processing for on-chain transaction monitoring
- RabbitMQ integration with Nemo Harbor
- 2FA authentication (TOTP via speakeasy)
- Market order execution with slippage tolerance

**Transaction Types Supported:**
- Stock buy/sell
- Token mint/burn
- Crypto deposits/withdrawals
- Fiat-to-stable conversions
- Wallet deposits/transfers

---

## Pre-Professional Projects

### Pixelnauts Racing Club (67 commits)
Endless runner browser game on Solana integrating Orcanauts NFTs. Players connect wallets containing NFTs or use a practice character. Built with TypeScript, React, Solana web3.js, Metaplex, and wallet adapters. Shipped to production at pixelnautsracingclub.so.

### Tac-Toe (94 commits, 10 GitHub stars)
Multiplayer on-chain tic-tac-toe with a React/TypeScript frontend and Rust/Anchor smart contract deployed on Solana devnet. Players connect wallets, create games, and play with moves submitted as blockchain transactions. Deployed to Vercel.

---

## Background

- **Previous Career**: Mechanical Designer at CWA Engineers (Nov 2017 – Sep 2021) — 3D modelling and design for industrial infrastructure
- **Education**: Mechanical Engineering Technology Diploma, BCIT (2015–2017)
- **Transition**: Self-taught software development part-time from mid-2020, then full-time from Sep 2021 to Apr 2022, building Solana dApps that led to the Step Finance role

