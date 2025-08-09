# Flash Swap Simulation - Pro (Hardhat)

Professional demo project for a controlled flash-swap simulation (educational / security training).
Created for use as a non-production, testnet-only proof-of-concept.

## Features
- Solidity (>=0.8.19) contracts:
  - `FlashSwapProvider.sol` - simple flash-swap provider that lends ERC20 tokens and expects repayment+fee in same tx.
  - `FlashSwapUser.sol` - example borrower implementing callback to repay.
  - `MockERC20.sol` - minimal ERC20 for tests and testnet demos.
- Hardhat setup: compile, test, deploy scripts
- Unit tests (Mocha/Chai) that assert provider receives repayment+fee.
- Optional React frontend to trigger a flash-swap from a connected wallet (included in `frontend/`).
- Clear comments, security notes, and no NDA/client code included.

## Quick start (local)
1. Install dependencies (node >=16):
```bash
npm install
npx hardhat compile
npx hardhat test
```

## Testnet deploy (example - Sepolia)
1. Set env vars:
```bash
export INFURA_KEY=your_infura_key
export DEPLOYER_KEY=your_private_key  # keep private
```
2. Deploy:
```bash
npx hardhat run --network sepolia scripts/deploy.js
```

## Security notes
- This is an educational demo only. Do NOT use on mainnet or with real funds.
- Fee is configurable in basis points on the provider; adjust as needed for demonstrations.
- The borrower must repay amount+fee within same transaction — otherwise the provider reverts.

## Frontend
A minimal React frontend is included to connect MetaMask and call the provider flashSwap via ethers.js. See `frontend/README.md` for usage.

## License
No license included (per request).

