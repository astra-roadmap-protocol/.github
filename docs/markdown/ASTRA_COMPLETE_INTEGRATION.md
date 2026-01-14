# ASTRA Complete Integration Blueprint
## Fork/Clone + Integration Guide (NOT Hyperkit)

**IMPORTANT**: This is for **ASTRA PROJECT ONLY** (AI learning platform). This is separate from Hyperkit.

---

## ASTRA Quick Overview

```
ASTRA (AI-Powered Learning Platform)
├── Smart Contracts (Chainlink Functions + ERC-8004)
├── Backend API (x402 payments + agent orchestration)
├── Frontend (Next.js + thirdweb Connect)
└── Multi-chain (Mantle, Solana, Arbitrum, Avalanche)
```

---

# START HERE: Repos to Fork/Clone Right Now

## Tier 1: Must Clone (Foundation)
```bash
cd astra-platform

# 1. Clone Chainlink Functions starter
git clone https://github.com/smartcontractkit/functions-hardhat-starter-kit.git contracts
cd contracts && npm install && npm install @openzeppelin/contracts && cd ..

# 2. Clone ERC-8004 agent registries
git clone https://github.com/vistara-apps/erc-8004-example.git erc8004-reference

# 3. Clone ERC-1066-X402 payment contracts
git clone https://github.com/Hyperkit-Labs/erc1066-x402.git x402-reference
```

## Tier 2: Backend Setup
```bash
# 4. Create backend (Node.js + Express)
mkdir backend && cd backend
npm init -y
npm install express cors dotenv ethers axios typescript ts-node nodemon
npm install @thirdweb-dev/payments-sdk @pinata/sdk
npm install -D @types/express @types/node
cd ..
```

## Tier 3: Frontend Setup
```bash
# 5. Create frontend (Next.js)
npx create-next-app@latest frontend --typescript --tailwind
cd frontend
npm install @thirdweb-dev/wallets @thirdweb-dev/react ethers
npx shadcn-ui@latest init && npx shadcn-ui@latest add card button form
cd ..
```

**Total setup time: 30 minutes**

---

# COMPLETE INTEGRATION GUIDE

## Layer 1: Smart Contracts (What to adopt)

### From Chainlink Starter (Keep as-is)
- ✅ `FunctionsClient.sol`
- ✅ `FunctionsRouter.sol`
- ✅ `hardhat.config.js` (extend, don't rewrite)
- ✅ Test suite structure

### From ERC-8004 Example (Copy these files)
```bash
# Copy into contracts/contracts/
cp erc8004-reference/contracts/IdentityRegistry.sol contracts/contracts/
cp erc8004-reference/contracts/ReputationRegistry.sol contracts/contracts/
cp erc8004-reference/contracts/ValidationRegistry.sol contracts/contracts/

# These track:
# - Agent identity (who is ASTRA)
# - Reputation scores (roadmap quality)
# - Validation (optional premium tier verification)
```

### From ERC-1066-X402 (Copy & modify)
```bash
# Copy into contracts/contracts/
cp x402-reference/contracts/x402PaymentProcessor.sol contracts/contracts/
cp x402-reference/contracts/StatusCodes.sol contracts/contracts/

# Modify x402PaymentProcessor.sol to add:
# function roadmapCost(uint tier) public view returns (uint256) { ... }
```

### What You Write
```bash
# contracts/contracts/ASTRAAgent.sol
# Extends FunctionsConsumer.sol from Chainlink starter
# Integrates:
# - Calls roadmap-generation.js on Chainlink DON
# - Updates ERC-8004 reputation on success
# - Emits IPFS hash
# - Settles x402 payment

contract ASTRAAgent is FunctionsClient {
    IdentityRegistry public identityRegistry;
    ReputationRegistry public reputationRegistry;
    X402PaymentProcessor public paymentProcessor;
    
    function generateRoadmap(string userProfile, string goal) 
        external 
        payable 
        returns (bytes32) 
    {
        // Charge x402 payment
        paymentProcessor.settlePayment(msg.sender, roadmapCost(msg.sender));
        
        // Request Chainlink Functions
        return _sendRequest(...);
    }
    
    function fulfillRequest(bytes32 requestId, bytes response, bytes err) 
        internal 
        override 
    {
        // Update reputation
        reputationRegistry.updateAgentScore(address(this), SUCCESS, ipfsHash);
    }
}
```

---

## Layer 2: Backend (What to adopt)

### From thirdweb x402 SDK (Use directly)
```typescript
// backend/src/middleware/x402Middleware.ts
import { PaymentMiddleware } from '@thirdweb-dev/payments-sdk';

const x402 = new PaymentMiddleware({
    chainId: 5003, // Mantle testnet
    treasuryAddress: process.env.ASTRA_TREASURY,
    supportedTokens: ['USDC']
});

// Use in routes:
// app.post('/api/roadmaps/generate', x402.verify(), controller);
```

### From Pinata SDK (Use directly)
```typescript
// backend/src/services/ipfsService.ts
import { PinataSDK } from '@pinata/sdk';

const pinata = new PinataSDK({
    pinataJwt: process.env.PINATA_JWT
});

export async function uploadRoadmap(data: any) {
    const result = await pinata.pinJSONToIPFS(data);
    return result.IpfsHash;
}
```

### From ERC-8004 Example (Query contract state)
```typescript
// backend/src/services/erc8004Service.ts
import { ethers } from 'ethers';
import REPUTATION_ABI from '../contracts/ReputationRegistry.json';

const reputationRegistry = new ethers.Contract(
    process.env.REPUTATION_ADDRESS,
    REPUTATION_ABI,
    provider
);

export async function getAgentScore() {
    return await reputationRegistry.getAgentScore(ASTRA_AGENT_ADDRESS);
}
```

### What You Write
```typescript
// backend/src/services/chainlinkService.ts
// Call ASTRAAgent.sol contract
// Listen for RoadmapGenerated events
// Fetch from IPFS when ready

// backend/src/routes/roadmap.routes.ts
// POST /api/roadmaps/generate (x402 protected)
// GET /api/roadmaps/:id
// GET /api/agent/reputation
```

---

## Layer 3: Frontend (What to adopt)

### From thirdweb Wallets (Drop-in component)
```typescript
// frontend/app/components/Header.tsx
import { ConnectWallet } from '@thirdweb-dev/react';

export default function Header() {
    return (
        <header>
            <h1>ASTRA</h1>
            <ConnectWallet 
                wallets={['MetaMask', 'Phantom']}
                theme="dark" 
            />
        </header>
    );
}
```

### From shadcn/ui (Pre-built components)
```typescript
// frontend/app/components/RoadmapForm.tsx
import { Card } from '@/components/ui/card';
import { Button } from '@/components/ui/button';
import { Input } from '@/components/ui/input';

export default function RoadmapForm() {
    return (
        <Card>
            <form>
                <Input placeholder="Current skills" />
                <Input placeholder="Learning goal" />
                <Button>Generate Roadmap</Button>
            </form>
        </Card>
    );
}
```

### What You Write
```typescript
// frontend/app/hooks/useRoadmap.ts
// POST to /api/roadmaps/generate
// Poll for result (Chainlink takes ~30 seconds)
// Fetch from IPFS when ready

// frontend/app/components/RoadmapDisplay.tsx
// Show 3 personalized options
// Display agent reputation score
```

---

# Integration Wiring Diagram

```
User fills form
    ↓
connectWallet() [thirdweb]
    ↓
POST /api/roadmaps/generate
    ↓
x402Middleware verifies payment [thirdweb x402]
    ↓
ASTRAAgent.generateRoadmap() [Chainlink Functions]
    ↓
Chainlink DON runs roadmap-generation.js
    ↓
ASTRAAgent.fulfillRequest()
    ↓
reputationRegistry.updateScore() [ERC-8004]
    ↓
pinata.uploadRoadmap() [Pinata SDK]
    ↓
Frontend polls GET /api/roadmaps/:id
    ↓
Display roadmap from IPFS
```

---

# File Mapping: What to Copy/Modify

| File | Source | Action | Reason |
|------|--------|--------|--------|
| `FunctionsConsumer.sol` | Chainlink starter | **MODIFY → ASTRAAgent.sol** | Add ERC-8004 + x402 integration |
| `IdentityRegistry.sol` | ERC-8004 example | **COPY** | Register ASTRA agent |
| `ReputationRegistry.sol` | ERC-8004 example | **COPY** | Track roadmap quality |
| `X402PaymentProcessor.sol` | ERC-1066-X402 | **COPY** | Handle payments |
| `roadmap-generation.js` | You write | **CREATE** | Call OpenAI, return roadmap |
| `x402Middleware.ts` | thirdweb example | **COPY/ADAPT** | Verify payment on all endpoints |
| `ipfsService.ts` | Pinata example | **COPY** | Upload roadmaps |
| `erc8004Service.ts` | You write | **CREATE** | Query reputation registries |
| `WalletConnect.tsx` | thirdweb | **DROP-IN** | No modification needed |
| `RoadmapForm.tsx` | You write | **CREATE** | shadcn/ui form |

---

# Dependency Tree (What Gets Installed)

```
astra-platform/
├── contracts/
│   └── @openzeppelin/contracts, @chainlink/contracts
├── backend/
│   ├── express, cors, dotenv, ethers, axios
│   ├── @thirdweb-dev/payments-sdk (x402)
│   └── @pinata/sdk (IPFS)
└── frontend/
    ├── next, react
    ├── @thirdweb-dev/wallets, @thirdweb-dev/react
    ├── ethers
    └── shadcn/ui
```

---

# Environment Variables (Minimal Set)

```bash
# contracts/.env
PRIVATE_KEY=0x...                              # MetaMask export
OPENAI_API_KEY=sk-...                         # OpenAI API
MANTLE_TESTNET_RPC=https://rpc.sepolia.mantle.xyz/
SUBSCRIPTION_ID=...                           # Chainlink dashboard

# backend/.env
PINATA_JWT=...                                # Pinata
THIRDWEB_API_KEY=...                          # thirdweb
ASTRA_AGENT_ADDRESS=0x...                     # Deployed contract
REPUTATION_ADDRESS=0x...                      # ERC-8004 registry

# frontend/.env.local
NEXT_PUBLIC_ASTRA_AGENT_ADDRESS=0x...
NEXT_PUBLIC_THIRDWEB_API_KEY=...
NEXT_PUBLIC_MANTLE_RPC=https://rpc.sepolia.mantle.xyz/
```

---

# 3-Week Implementation Timeline

## Week 1: Smart Contracts
```bash
Day 1: Clone Chainlink starter, verify it compiles
Day 2: Copy ERC-8004 + x402 contracts
Day 3: Write ASTRAAgent.sol (modify FunctionsConsumer)
Day 4: Write roadmap-generation.js
Day 5: Deploy to Mantle testnet, test
```

## Week 2: Backend
```bash
Day 6: Setup Express + install thirdweb + Pinata SDKs
Day 7: Create x402Middleware
Day 8: Create ipfsService + erc8004Service
Day 9: Create chainlinkService
Day 10: Test payment → Chainlink → IPFS → reputation flow
```

## Week 3: Frontend
```bash
Day 11: Setup Next.js, install thirdweb wallets + shadcn
Day 12: Build Header with ConnectWallet
Day 13: Build RoadmapForm with shadcn/ui
Day 14: Build RoadmapDisplay + useRoadmap hook
Day 15: End-to-end testing
```

---

# Next Immediate Actions

1. **TODAY**: Run the 3 Clone commands above
2. **Tomorrow**: Copy contracts from erc8004-reference and x402-reference
3. **Day 3**: Write ASTRAAgent.sol
4. **Day 4**: Deploy to testnet
5. **Day 5**: Start backend

---

# Summary: Adopt vs Build

```
Smart Contracts
├── ✅ Adopt: FunctionsClient.sol (Chainlink)
├── ✅ Adopt: IdentityRegistry.sol (ERC-8004)
├── ✅ Adopt: ReputationRegistry.sol (ERC-8004)
├── ✅ Adopt: X402PaymentProcessor.sol (x402)
├── 🔴 Build: ASTRAAgent.sol (your contract)
└── 🔴 Build: roadmap-generation.js (your JS)

Backend
├── ✅ Adopt: x402Middleware (thirdweb)
├── ✅ Adopt: ipfsService (Pinata)
├── 🔴 Build: chainlinkService
├── 🔴 Build: erc8004Service
└── 🔴 Build: routes + controllers

Frontend
├── ✅ Adopt: ConnectWallet (thirdweb)
├── ✅ Adopt: Card, Button, Form (shadcn)
├── 🔴 Build: RoadmapForm
├── 🔴 Build: RoadmapDisplay
└── 🔴 Build: useRoadmap hook
```

**Result: 65% adopted code, 35% custom code**

---

Good luck! This is your ASTRA blueprint. 🚀