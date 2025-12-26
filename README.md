## 🛠️ Technology

### Blockchain & Smart Contracts
- **Sui Network** — High-performance Layer 1 blockchain
- **Move** — Secure smart contract language
- **Shared Objects** — Allows concurrent access

### User Interface
- **React 18**
- **TypeScript**
- **@mysten/dapp-kit**
- **@mysten/sui**
- **React Query**

### Development Tools

- **Node.js**

- **npm**

- **Sui CLI**

---
## 📥 Installation

### Version

-- **Node.js** v16 or higher
- **npm** or **yarn**
- **Sui CLI** (for smart contract development)
- **Git**

### 1: Clone the repository

```bash
git clone https://github.com/yourusername/charity-dapp.git
cd charity-dapp
```

### Step 2: Install Dependencies

``` bash
# Install the entire project (frontend + move)
install npm --legacy-peer-deps

# Or install in parts
# UI
interface cd
install npm --legacy-peer-deps

# Migrate (if needed)
cd ../migrate
sui move build
```

### Step 3: Configure Sui

``` bash
# Sui settings (if not already present)
sui new client

# Select test network
# Choose to create a new wallet or use an existing wallet
```

### Step 4: Deploy Smart Contract

``` bash
move cd

# contract build
sui move build

# Publish contract on testnet
Depending on the publishing client --gas-budget 100000000

# Save packet address from output
# Update frontend/src/config/constants.ts
```

### Step 5: Run Frontend

``` bash
interface cd
start npm

# The application will open at: http://localhost:3000
```

---
## 💻 Tool Usage Guide

### Main User Process

#### 1️⃣ Connect Sui Wallet
```
1. Access http://localhost:3000
2. Click "Connect Wallet"
3. Choose your Sui wallet
4. Approve the connection request
```

#### 2️⃣ Create Campaign
```
1. Click "Create Campaign"
2. Fill in the information: - Title: Improved Campaign Name
- Description: Objective Details
- Objective (SUI): Amount to cause annoyance
- Beneficiary: SUI address to receive money
- Subtotal: Campaign End Date
3. "Create"
4. Approve transaction in wallet
5. Wait for confirmation (2-3 seconds)
```

#### 3️⃣ Donate to a Campaign
```
1. View the list of services on the homepage
2. Select the campaign you want to donate to
3. Click the "Donate" button
4. Enter the amount of SUI
5. Approve the transaction
6. View the real-time excess update
```

#### 4️⃣ Withdraw (Creator/Beneficiary Only)
```
1. Open your campaign
2. Click the "Withdraw" button
3. Approve the transaction
4. Money is received Transfer to beneficiary's wallet
```

---
## 🔧 Development

### Working with Smart Contracts

#### Editing Contracts
``` bash
move cd
# Edit source/charity.move

# Rebuild
sui move build
# Run tests
test move sui

# Publish
sui client publish --gas-budget 100000000
```

#### Move Contract Structure

``` move
charity::charity_platform module {
// Main structure:

// 1. CampaignRegistry (Shared Object)
// - Stores a list of all campaign IDs

// 2. Campaign (Shared Object)
// - Title, description, objective
// - Amount raised (Number (SUI)

// - Happiness, creator, beneficiary

// Main functions:

// - create_campaign() - Create a new campaign
// - donate() - Donate to a campaign
// - draw_funds() - Withdraw money (authorized users only)

// - get_campaign_info() - Get campaign information
}
```

### Working with Frontend

#### Configuring the Frontend

``` typed
// Homepage - Display campaign list
component/CampaignList.tsx

// Create campaign
page/CreateCampaignPage.tsx

component/CreateCampaignForm.tsx

// Details & Donations
component/CampaignCard.tsx

component/DonateModal.tsx

// Statistics
component part/StatsBar.tsx

```
####Connecting to Sui

``` typed
// Using a Custom Hook
import { useSui } from '../hooks/useSui';

function MyComponent() {
const { wallet, connected } = useSui();

// Calling the Smart Contract Function
const handDonate = async(quantity: string) => {
// Interacting with the Smart Contract
};

}
```

#### Calling Smart Contracts

```typescript
// utils/suiTransactions.ts
export async function createCampaign(

title: string,

description: string,

goal: number,

deadline: number,

beneficiary: string

) {

// Call the move entry function: create_campaign

// Return transaction ID

}

export async function donate(

campaignId: string,

amount: number

) {

// Call the move entry function: donate

}
```

---
## 🚀 Deployment

### Deployment Testnet
```bash
# 1. Build the Move contract
cd move
sui move build
# 2. Publish to testnet
sui client publish --gas-budget 100000000

# 3. Save Package address from output
# Example: 0x1a2b3c4d5e6f...

# 4. Update frontend
# src/config/constants.ts
export const PACKAGE_ID = "0x1a2b3c4d5e6f...";


```

### Declare Frontend (Mainnet)

```bash
cd frontend

# Build for production
npm run build

# Output: build/folder

# Deploy to hosting
# - Vercel: vercel deploy
# - Netlify: netlify deploy
# - GitHub Pages: npm run build && git push
```

---
## 📊 API Reference

### Smart Contract Functionality

#### `create_camp