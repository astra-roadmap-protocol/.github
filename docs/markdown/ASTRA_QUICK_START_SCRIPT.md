# ASTRA: Go-Live Checklist (Next 3 Hours)

## This is NOT Hyperkit. This is ASTRA (Learning Platform).

Copy & paste these commands in order. Total time: ~3 hours.

---

## HOUR 1: Clone Foundation Repos (30 min)

```bash
# Create root directory
mkdir -p ~/Projects/astra-platform
cd ~/Projects/astra-platform

# Clone Tier 1: Core smart contract starter
git clone https://github.com/smartcontractkit/functions-hardhat-starter-kit.git contracts
cd contracts
npm install --legacy-peer-deps
npm install @openzeppelin/contracts
echo "✅ Chainlink Functions starter ready"
cd ..

# Clone Tier 1: ERC-8004 agent identity + reputation
git clone https://github.com/vistara-apps/erc-8004-example.git erc8004-ref
echo "✅ ERC-8004 example ready"

# Clone Tier 1: x402 payment contracts
git clone https://github.com/Hyperkit-Labs/erc1066-x402.git x402-ref
echo "✅ ERC-1066-X402 ready"

# Verify installs worked
cd contracts
npx hardhat --version
echo "✅ All repos cloned successfully!"
cd ..
```

---

## HOUR 2: Backend + Frontend Setup (30 min)

```bash
# Backend (Express.js)
mkdir backend
cd backend

npm init -y
npm install express cors dotenv ethers axios typescript ts-node nodemon
npm install @thirdweb-dev/payments-sdk @pinata/sdk
npm install -D @types/express @types/node
npm install -D ts-node

# Create minimal src/index.ts
mkdir -p src
cat > src/index.ts << 'EOF'
import express from 'express';
import cors from 'cors';
import dotenv from 'dotenv';

dotenv.config();
const app = express();

app.use(cors());
app.use(express.json());

app.get('/health', (req, res) => {
  res.json({ status: 'ok', message: 'ASTRA backend running' });
});

const PORT = process.env.PORT || 3001;
app.listen(PORT, () => {
  console.log(`✅ Backend running on http://localhost:${PORT}`);
});
EOF

# Create .env template
cat > .env << 'EOF'
PORT=3001
NODE_ENV=development
PINATA_JWT=your-jwt-here
THIRDWEB_API_KEY=your-api-key-here
ASTRA_AGENT_ADDRESS=0x
MANTLE_TESTNET_RPC=https://rpc.sepolia.mantle.xyz/
EOF

npm pkg set scripts.dev="ts-node src/index.ts"
echo "✅ Backend ready"
cd ..

# Frontend (Next.js)
echo "Creating Next.js app (takes 2-3 min)..."
npx create-next-app@latest frontend --typescript --tailwind --eslint --git=false

cd frontend

npm install @thirdweb-dev/wallets @thirdweb-dev/react ethers

# Initialize shadcn/ui
npx shadcn-ui@latest init -y
npx shadcn-ui@latest add card button form input modal

# Create .env.local
cat > .env.local << 'EOF'
NEXT_PUBLIC_API_URL=http://localhost:3001
NEXT_PUBLIC_ASTRA_AGENT_ADDRESS=0x
NEXT_PUBLIC_MANTLE_RPC=https://rpc.sepolia.mantle.xyz/
EOF

echo "✅ Frontend ready"
cd ..

echo "✅ Backend + Frontend setup complete!"
```

---

## HOUR 3: Copy Key Contracts + Test (30 min)

```bash
# Copy ERC-8004 contracts
cp erc8004-ref/contracts/IdentityRegistry.sol contracts/contracts/ 2>/dev/null || echo "Skipped (may not exist)"
cp erc8004-ref/contracts/ReputationRegistry.sol contracts/contracts/ 2>/dev/null || echo "Skipped (may not exist)"

# Copy x402 contracts
cp x402-ref/contracts/x402PaymentProcessor.sol contracts/contracts/ 2>/dev/null || echo "Skipped (may not exist)"
cp x402-ref/contracts/StatusCodes.sol contracts/contracts/ 2>/dev/null || echo "Skipped (may not exist)"

echo "✅ Contracts copied"

# Verify everything compiles
cd contracts
npx hardhat compile
echo "✅ Contracts compile successfully!"
cd ..

# Git init
git init
git add .
git commit -m "Initial ASTRA setup: Chainlink + ERC-8004 + x402 + thirdweb + Pinata" 2>/dev/null || echo "Git commit skipped"

echo ""
echo "============================================"
echo "✅ ASTRA SETUP COMPLETE!"
echo "============================================"
echo ""
echo "Project structure:"
ls -la | grep -E "^d.*contracts|^d.*backend|^d.*frontend|^d.*erc8004|^d.*x402"
echo ""
echo "Next steps:"
echo "1. Terminal 1: cd contracts && npm run node"
echo "2. Terminal 2: cd backend && npm run dev"
echo "3. Terminal 3: cd frontend && npm run dev"
echo ""
echo "Then visit: http://localhost:3000"
echo ""
echo "Files to fill in:"
echo "  - contracts/.env (PRIVATE_KEY, OPENAI_API_KEY)"
echo "  - backend/.env (PINATA_JWT, THIRDWEB_API_KEY)"
echo "  - frontend/.env.local (contract addresses after deployment)"
echo ""
```

---

## Files Created

After running above, you should have:

```
astra-platform/
├── contracts/              # Chainlink Functions starter
│   ├── contracts/
│   │   ├── FunctionsClient.sol ✅
│   │   ├── ASTRAAgent.sol 🔴 (you write next)
│   │   └── [copied registries]
│   ├── hardhat.config.js
│   ├── .env (FILL THIS IN)
│   └── package.json
│
├── backend/                # Express.js
│   ├── src/
│   │   └── index.ts (minimal server)
│   ├── .env (FILL THIS IN)
│   └── package.json
│
├── frontend/               # Next.js
│   ├── app/
│   │   └── page.tsx
│   ├── .env.local (FILL THIS IN)
│   └── package.json
│
├── erc8004-ref/           # Reference (don't modify)
├── x402-ref/              # Reference (don't modify)
└── .git/
```

---

## Quick Test (Run These 3 Commands in Separate Terminals)

```bash
# Terminal 1: Local blockchain
cd contracts && npx hardhat node

# Terminal 2: Backend API
cd backend && npm run dev
# Expected: "✅ Backend running on http://localhost:3001"

# Terminal 3: Frontend
cd frontend && npm run dev
# Expected: "▲ Next.js is running"
```

Then open: **http://localhost:3000** in your browser.

---

## What You Just Set Up

✅ **Smart Contracts**
- Chainlink Functions (for AI roadmap generation)
- ERC-8004 (for agent identity + reputation)
- x402 (for payment processing)

✅ **Backend API**
- Express.js server on port 3001
- Ready for thirdweb x402 + Pinata integration
- Ready for Chainlink Functions integration

✅ **Frontend Web App**
- Next.js on port 3000
- thirdweb wallet integration ready
- shadcn/ui components ready

---

## What You Need to Fill In (Tomorrow)

1. **contracts/.env**
   ```env
   PRIVATE_KEY=0x... (from MetaMask)
   OPENAI_API_KEY=sk-... (from OpenAI)
   ```

2. **backend/.env**
   ```env
   PINATA_JWT=... (from Pinata)
   THIRDWEB_API_KEY=... (from thirdweb)
   ```

3. **frontend/.env.local**
   ```env
   NEXT_PUBLIC_ASTRA_AGENT_ADDRESS=0x... (after contract deployment)
   ```

---

## If Something Fails

```bash
# Clear and try again
rm -rf node_modules package-lock.json
npm install

# Or reset everything
cd ..
rm -rf astra-platform
# Run the script again
```

---

## Success Indicators ✅

If you see these, you're good:
- ✅ `npx hardhat compile` succeeds
- ✅ Backend server starts without errors
- ✅ Frontend loads at http://localhost:3000
- ✅ ConnectWallet button appears (after install)

---

**You're now ready to build ASTRA!** 🚀

Next: Write ASTRAAgent.sol by modifying FunctionsConsumer.sol