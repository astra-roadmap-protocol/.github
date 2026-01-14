# ASTRA Project: Concrete Fork/Clone Blueprint
## "Adopt vs Build" Repos for Agents + Infrastructure

---

## ASTRA PROJECT OVERVIEW
**ASTRA** = AI-powered personalized learning platform on Web3
- **Core**: Chainlink Functions (AI roadmap generation via OpenAI)
- **Payments**: x402 (usage-based billing for API calls)
- **Agents**: ERC-8004 agent identity + reputation
- **Storage**: IPFS/Pinata (roadmap content)
- **Multi-chain**: EVM (Mantle, Arbitrum, Avalanche) + Solana

---

# PART 1: CORE REPOS TO FORK/CLONE

## Layer 1: Smart Contracts Foundation

### 1. **Chainlink Functions Hardhat Starter** (CLONE)
```bash
git clone https://github.com/smartcontractkit/functions-hardhat-starter-kit.git astra-contracts
cd astra-contracts
npm install
npm install @openzeppelin/contracts
```

**What to keep**: FunctionsClient.sol, FunctionsRouter.sol, hardhat.config.js (as base)  
**What to modify**: Create ASTRAAgent.sol extending FunctionsConsumer.sol  
**Why**: Complete Chainlink Functions setup. Don't rebuild this.

---

### 2. **ERC-8004 Agent Registry** (FORK)
```bash
git clone https://github.com/vistara-apps/erc-8004-example.git astra-erc8004
cd astra-erc8004
```

**Adopt these contracts**:
- `IdentityRegistry.sol` → Register ASTRA agent identity
- `ReputationRegistry.sol` → Track roadmap success/failure scores
- `ValidationRegistry.sol` → Optional validator flows for premium content

**Where it plugs in**:
```solidity
// In ASTRAAgent.sol fulfillRequest():
function fulfillRequest(bytes32 requestId, bytes response, bytes err) internal {
    // ... roadmap generation logic ...
    
    // Update ERC-8004 reputation
    reputationRegistry.updateAgentScore(
        address(this),
        SUCCESS_SCORE,
        ipfsHash
    );
    
    emit RoadmapGenerated(requestId, ipfsHash);
}
```

**Why fork instead of clone**: You'll modify the interface to emit IPFS hashes + integrate with x402 settlement.

---

### 3. **ERC-1066-X402 Payment Contracts** (CLONE/ADAPT)
```bash
git clone https://github.com/Hyperkit-Labs/erc1066-x402.git astra-billing
cd astra-billing
```

**What to keep**:
- `x402PaymentProcessor.sol` (billing logic)
- `StatusCodes.sol` (ERC-1066 for policy checks)

**What to modify**: Add `roadmapCost` function + ASTRA-specific pricing tiers.

**Where it plugs in**:
```solidity
// In backend x402 middleware:
const cost = await contract.roadmapCost(userTier);
// Charge USDC before Chainlink Functions call
```

**Why**: Don't rebuild payment logic. They've already audited x402 settlement.

---

## Layer 2: Backend Infrastructure

### 4. **thirdweb x402 SDK** (NPM + integrate)
```bash
cd astra-backend
npm install @thirdweb-dev/payments-sdk
npm install @thirdweb-dev/wallets
npm install @thirdweb-dev/engine
```

**Core files to adopt**:
- `PaymentMiddleware.ts` (thirdweb x402 example)
- `SettlementService.ts` (thirdweb payment settlement)

**Template code**:
```typescript
// backend/src/middleware/x402Middleware.ts
import { PaymentMiddleware } from '@thirdweb-dev/payments-sdk';

const x402 = new PaymentMiddleware({
    chainId: MANTLE_CHAIN_ID,
    treasuryAddress: ASTRA_TREASURY,
    supportedTokens: ['USDC']
});

// Use in route:
app.post('/api/roadmaps/generate', x402.verify(), roadmapController.generate);
```

**Where it plugs in**:
- All API endpoints that cost money (generate roadmap, get premium content)
- Automatic payment settlement on `402 Payment Required` response

**Why**: 100% battle-tested. thirdweb handles wallet negotiation + token settlement.

---

### 5. **Pinata IPFS SDK** (NPM)
```bash
npm install @pinata/sdk
npm install ipfs-http-client (optional backup)
```

**Core method**:
```typescript
// backend/src/services/ipfsService.ts
import { PinataSDK } from '@pinata/sdk';

const pinata = new PinataSDK({
    pinataJwt: process.env.PINATA_JWT
});

export async function uploadRoadmap(roadmapData: any) {
    const result = await pinata.pinJSONToIPFS(roadmapData);
    return result.IpfsHash; // e.g., "QmXxxx..."
}
```

**Where it plugs in**:
```typescript
// In fulfillRequest callback:
const ipfsHash = await ipfsService.uploadRoadmap(roadmapJSON);
await reputationRegistry.updateAgentScore(
    address(this),
    SUCCESS_SCORE,
    ipfsHash
);
```

**Why**: Zero infra cost. Pinata handles IPFS pinning + gateway.

---

## Layer 3: Frontend UI Components

### 6. **thirdweb Connect Wallet SDK** (NPM + adopt components)
```bash
cd astra-frontend
npm install @thirdweb-dev/wallets
npm install @thirdweb-dev/react
npm install @thirdweb-dev/ui
```

**Drop-in components**:
- `<ConnectWallet />` button (replaces wagmi/rainbowkit boilerplate)
- `useContract` hook (from @thirdweb-dev/react)
- `useAddress`, `useUser` (wallet state)

**Template code**:
```typescript
// frontend/app/components/WalletConnect.tsx
import { ConnectWallet } from '@thirdweb-dev/react';

export default function Header() {
    return (
        <nav>
            <h1>ASTRA</h1>
            <ConnectWallet
                wallets={['MetaMask', 'Phantom', 'WalletConnect']}
                theme="dark"
            />
        </nav>
    );
}
```

**Where it plugs in**: All pages that need wallet connection.

**Why**: Single component handles all wallet networks (Mantle, Solana, Arbitrum, Avalanche).

---

### 7. **shadcn/ui Components** (NPM + scaffold)
```bash
cd astra-frontend
npx shadcn-ui@latest init
npx shadcn-ui@latest add card button form input modal stepper
```

**Use for**:
- `Card` (roadmap result display)
- `Form` + `Input` (questionnaire)
- `Stepper` (learning progression UI)
- `Modal` (payment confirmation)

**Why**: Pre-built, accessible, Tailwind-compatible. Faster than custom Tailwind.

---

## Layer 4: Multi-Chain Specific

### 8. **Solana Anchor Framework** (CLONE if Solana program needed)
```bash
anchor init astra-solana
cd astra-solana
```

**Use only if you need**:
- Solana program (on-chain logic)
- SPL token interactions (not just wallet login)

**Otherwise skip** (Solana can be just wallet login + x402 settlement).

**Where it plugs in**:
- If ASTRA offers Solana-native features (e.g., Solana reputation NFTs, Solana DAO payouts)
- Otherwise: Use `@solana/web3.js` v2 for wallet signing only

---

### 9. **Mantle Mosaic** (CLONE as reference, optional)
```bash
git clone https://github.com/harishkotra/mosaic.git mantle-reference
# Read for Mantle-specific gas optimization tips
```

**What to use**:
- Gas optimization patterns for Mantle (very cheap already)
- Mantle network config examples

**Why clone?**: Documentation is in the repo; reference for Mantle testnet setup.

---

# PART 2: AGENT ORCHESTRATION REPOS

### 10. **CrewAI with ERC-8004** (NPM + fork example)
```bash
# Clone the vistara example that includes CrewAI integration
git clone https://github.com/vistara-apps/erc-8004-example.git
# Look for: examples/crewai_agent_example.py

# Install CrewAI
pip install crewai
pip install crewai-tools
```

**Where it plugs in**:
- **Post-Chainlink workflow**: After roadmap is generated on-chain, trigger CrewAI agents
- Agent 1: Analyze roadmap quality
- Agent 2: Validate learning outcomes
- Agent 3: Update reputation on-chain

```python
# backend/agents/validation_agent.py
from crewai import Agent, Task, Crew
from erc_8004_client import ReputationRegistry

class RoadmapValidator(Agent):
    def validate(self, roadmap_data, ipfs_hash):
        # CrewAI analysis
        quality_score = self.analyze_content(roadmap_data)
        
        # Update ERC-8004
        registry = ReputationRegistry()
        registry.update_score(self.agent_id, quality_score, ipfs_hash)
```

**Why**: Multi-agent orchestration is complex. CrewAI handles it.

---

### 11. **Fetch.ai uAgents** (NPM + Python agents)
```bash
npm install @fetchai/uagents
pip install fetchai
```

**Where it plugs in** (optional advanced):
- Decentralized agent coordination across ASTRA instances
- Peer-to-peer agent discovery for study groups
- Micropayments between agents (utility tokens)

**Skip for MVP** (add later for decentralized multi-agent marketplace).

---

# PART 3: FORK VS CLONE DECISION TABLE

| Repo | Purpose | Action | Why |
|------|---------|--------|-----|
| **smartcontractkit/functions-hardhat-starter-kit** | Chainlink base | CLONE | Use as-is for deployment |
| **vistara-apps/erc-8004-example** | Agent registries | FORK | Modify contracts for ASTRA specifics |
| **Hyperkit-Labs/erc1066-x402** | Payment logic | CLONE/ADAPT | Use contracts, modify pricing |
| **@thirdweb-dev/payments-sdk** | x402 payments | NPM INSTALL | No cloning needed; library usage |
| **@pinata/sdk** | IPFS storage | NPM INSTALL | No cloning needed; library usage |
| **@thirdweb-dev/wallets** | Wallet UX | NPM INSTALL | No cloning needed; components only |
| **vistara-apps/erc-8004-example** (CrewAI) | Agent orchestration | CLONE | Reference + adapt to Python backend |
| **harishkotra/mosaic** | Mantle optimization | CLONE (ref only) | Read for tips, not core |
| **anchor-lang/examples** | Solana (optional) | SKIP for MVP | Only if Solana program needed |

---

# PART 4: COMPLETE ASTRA FILE TREE (After All Forks/Clones)

```
astra-platform/
│
├── contracts/                          # From smartcontractkit/functions-hardhat-starter-kit
│   ├── contracts/
│   │   ├── ASTRAAgent.sol             # 🔴 You modify FunctionsConsumer.sol
│   │   ├── IdentityRegistry.sol       # 📌 From vistara/erc-8004-example
│   │   ├── ReputationRegistry.sol     # 📌 From vistara/erc-8004-example
│   │   ├── ValidationRegistry.sol     # 📌 From vistara/erc-8004-example
│   │   ├── X402PaymentProcessor.sol  # 📌 From Hyperkit-Labs/erc1066-x402
│   │   └── StatusCodes.sol            # 📌 From Hyperkit-Labs/erc1066-x402
│   ├── functions/sources/
│   │   └── roadmap-generation.js      # 🔴 You write (calls OpenAI)
│   └── hardhat.config.js              # 🔴 You modify (add networks)
│
├── backend/                            # Node.js + Express
│   ├── src/
│   │   ├── middleware/
│   │   │   ├── x402Middleware.ts      # 📌 Adapt from @thirdweb-dev/payments-sdk
│   │   │   └── auth.middleware.ts     # 🔴 You write
│   │   ├── services/
│   │   │   ├── ipfsService.ts         # 📌 Using @pinata/sdk
│   │   │   ├── erc8004Service.ts      # 📌 Call deployed registries
│   │   │   ├── chainlinkService.ts    # 🔴 You write (call ASTRAAgent)
│   │   │   └── openaiService.ts       # 🔴 You write (call OpenAI, then Chainlink)
│   │   ├── routes/
│   │   │   ├── roadmap.routes.ts      # 🔴 You write (x402 protected)
│   │   │   ├── agent.routes.ts        # 🔴 You write (CrewAI orchestration)
│   │   │   └── reputation.routes.ts   # 🔴 You write (query ERC-8004)
│   │   └── agents/
│   │       ├── validation_agent.py    # 📌 Adapt from vistara/erc-8004-example
│   │       └── feedback_agent.py      # 🔴 You write (CrewAI)
│   └── package.json
│       # Key deps: @thirdweb-dev/payments-sdk, @pinata/sdk, ethers, crewai
│
├── frontend/                           # Next.js + React
│   ├── app/
│   │   ├── components/
│   │   │   ├── WalletConnect.tsx      # 📌 Using @thirdweb-dev/wallets
│   │   │   ├── RoadmapForm.tsx        # 🔴 You write (shadcn/ui)
│   │   │   ├── RoadmapCard.tsx        # 📌 Using shadcn Card component
│   │   │   ├── PaymentModal.tsx       # 📌 Using @thirdweb-dev/payments-ui (x402)
│   │   │   └── AgentStatus.tsx        # 🔴 You write
│   │   └── hooks/
│   │       ├── useWallet.tsx          # 📌 From @thirdweb-dev/react
│   │       ├── useContract.tsx        # 📌 From @thirdweb-dev/react
│   │       ├── usePayment.tsx         # 📌 From @thirdweb-dev/payments-sdk
│   │       └── useRoadmap.tsx         # 🔴 You write
│   └── package.json
│       # Key deps: @thirdweb-dev/wallets, @thirdweb-dev/react, shadcn/ui
│
└── docs/
    ├── FORKING_GUIDE.md               # 🔴 You write (this blueprint)
    └── INTEGRATION_CHECKLIST.md       # 🔴 You write
```

Legend:
- 📌 = From fork/clone (Adopted)
- 🔴 = You must write
- ✅ = Pre-generated by tools

---

# PART 5: EXACT BASH COMMANDS TO RUN NOW

## Setup (30 minutes)

```bash
# 1. Create root directory
mkdir astra-platform && cd astra-platform

# 2. Clone Chainlink starter (smart contracts)
git clone https://github.com/smartcontractkit/functions-hardhat-starter-kit.git contracts
cd contracts && npm install && npm install @openzeppelin/contracts && cd ..

# 3. Fork ERC-8004 (agent registries)
git clone https://github.com/vistara-apps/erc-8004-example.git erc8004-reference
# You'll cherry-pick contracts from here into contracts/contracts/

# 4. Fork ERC-1066-X402 (payment contracts)
git clone https://github.com/Hyperkit-Labs/erc1066-x402.git x402-reference
# You'll cherry-pick X402PaymentProcessor.sol into contracts/contracts/

# 5. Create backend
mkdir backend && cd backend
npm init -y
npm install \
  express cors dotenv ethers axios \
  @thirdweb-dev/payments-sdk @thirdweb-dev/wallets \
  @pinata/sdk \
  typescript ts-node nodemon \
  @types/express @types/node
npm install -D crewai  # Optional for agents
cd ..

# 6. Create frontend
npx create-next-app@latest frontend --typescript --tailwind
cd frontend
npm install \
  @thirdweb-dev/wallets @thirdweb-dev/react \
  @thirdweb-dev/ui \
  ethers \
  shadcn-ui zod react-hook-form
npx shadcn-ui@latest init
npx shadcn-ui@latest add card button form input modal stepper
cd ..

# 7. Create git repo
git init
git add .
git commit -m "Initial ASTRA setup: Chainlink + ERC-8004 + x402 + Pinata"
```

## After Setup: Copy Key Files

```bash
# Copy ERC-8004 contracts
cp erc8004-reference/contracts/IdentityRegistry.sol contracts/contracts/
cp erc8004-reference/contracts/ReputationRegistry.sol contracts/contracts/
cp erc8004-reference/contracts/ValidationRegistry.sol contracts/contracts/

# Copy x402 contracts
cp x402-reference/contracts/x402PaymentProcessor.sol contracts/contracts/
cp x402-reference/contracts/StatusCodes.sol contracts/contracts/

# Update package.json with Pinata JWT
echo 'PINATA_JWT=your-jwt-here' >> backend/.env
echo 'THIRDWEB_API_KEY=your-key-here' >> backend/.env
```

---

# PART 6: WHICH REPOS ARE REQUIRED vs OPTIONAL

| Repo | Required? | Why |
|------|-----------|-----|
| Chainlink Functions starter | ✅ YES | Foundation for Chainlink integration |
| ERC-8004 (vistara) | ✅ YES | Agent identity + reputation |
| ERC-1066-X402 (Hyperkit) | ✅ YES | Payment processing |
| thirdweb x402 SDK | ✅ YES | Client-side payment UX |
| Pinata IPFS | ✅ YES | Store roadmaps off-chain |
| thirdweb wallets | ✅ YES | Multi-chain wallet support |
| shadcn/ui | ✅ YES | Frontend components |
| CrewAI + erc8004 | ⏸️ OPTIONAL | Post-Chainlink agent orchestration (add later) |
| Fetch.ai | ❌ SKIP MVP | Decentralized agent mesh (Phase 2) |
| Anchor (Solana) | ❌ SKIP MVP | Only if Solana programs needed |
| Mantle Mosaic | ❌ SKIP | Reference only, not required |

---

# PART 7: INTEGRATION CHECKLIST

### Week 1: Smart Contracts
- [ ] Clone Chainlink starter, verify `npx hardhat compile` works
- [ ] Clone ERC-8004 example, copy registries to contracts/
- [ ] Clone ERC-1066-X402, copy payment logic
- [ ] Create ASTRAAgent.sol extending FunctionsConsumer
- [ ] Deploy all contracts to Mantle testnet
- [ ] Test ERC-8004 registry updates work

### Week 2: Backend
- [ ] Install thirdweb x402 SDK
- [ ] Create x402Middleware for all paid endpoints
- [ ] Install Pinata SDK, test file upload
- [ ] Create erc8004Service to query registries
- [ ] Create chainlinkService to request roadmaps
- [ ] Test end-to-end: payment → Chainlink → IPFS → reputation update

### Week 3: Frontend
- [ ] Install thirdweb wallets, test ConnectWallet button
- [ ] Build RoadmapForm using shadcn/ui
- [ ] Build RoadmapCard using shadcn Card
- [ ] Wire form → API call (x402 payment)
- [ ] Display results from IPFS
- [ ] Show agent reputation scores

---

# PART 8: KEY ENVIRONMENT VARIABLES

```bash
# contracts/.env
PRIVATE_KEY=0x...
OPENAI_API_KEY=sk-...
MANTLE_TESTNET_RPC=https://rpc.sepolia.mantle.xyz/

# backend/.env
PINATA_JWT=...
THIRDWEB_API_KEY=...
ASTRA_AGENT_ADDRESS=0x... (after deployment)
ERC8004_REPUTATION_ADDRESS=0x... (after deployment)
X402_PROCESSOR_ADDRESS=0x... (after deployment)

# frontend/.env.local
NEXT_PUBLIC_ASTRA_AGENT_ADDRESS=0x...
NEXT_PUBLIC_THIRDWEB_API_KEY=...
NEXT_PUBLIC_MANTLE_TESTNET_RPC=https://rpc.sepolia.mantle.xyz/
```

---

# SUMMARY: WHAT YOU CLONE, FORK, OR INSTALL

| Component | Action | Repository |
|-----------|--------|-----------|
| Chainlink Functions | **CLONE** | smartcontractkit/functions-hardhat-starter-kit |
| ERC-8004 Contracts | **FORK** | vistara-apps/erc-8004-example |
| x402 Payment Logic | **FORK** | Hyperkit-Labs/erc1066-x402 |
| thirdweb x402 SDK | **NPM INSTALL** | @thirdweb-dev/payments-sdk |
| Pinata IPFS | **NPM INSTALL** | @pinata/sdk |
| thirdweb Wallets | **NPM INSTALL** | @thirdweb-dev/wallets |
| shadcn/ui | **NPX SCAFFOLD** | shadcn-ui |
| CrewAI (optional) | **PIP INSTALL** | crewai + vistara example |

**Result**: 70% of ASTRA is adopted code. You only write 30% (product logic, UI, orchestration).

---

Good luck! You now have the exact repos. Go build! 🚀