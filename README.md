# paj_ramp

Paj Ramp is a crypto offramp API designed to allow users to convert Solana-based digital assets to fiat and transfer the resulting funds to traditional bank accounts. This backend service acts as a bridge between the Solana blockchain and the traditional banking system, enabling secure, authenticated, and user-friendly offboarding of funds from Web3 to Web2.

> _A simple wrapper for communicating with paj_ramp's backend endpoints — no manual API calls required._

### _“Send SOL. Get Naira.”_

> _The goal is to let users withdraw their crypto holdings from a Solana wallet and receive fiat currency in their linked bank accounts — all through a simple, authenticated API integration._

---

## 🚀 Features

- ✅ Easy-to-use functions for all backend endpoints
- 🔐 Handles Session Management
- 🧱 Clean, modular API
- 🕊️ No need to write `fetch()` or `axios` manually
- 🕸️ Handles Bank Operations like getting banks, adding banks, resolving banks and getting banks linked to the account

---

## 📦 Installation

```bash
# With npm
npm install paj_ramp

# With yarn
yarn add paj_ramp
```

---

## 📘 Usage Examples

### Get tx pool address

```bash
import { getTXPoolAddress } from 'paj_ramp';

const txpooladdress = await getTXPoolAddress();

# Response
{
  address: string,
}
```

### Get rate

```bash
import { getRate } from 'paj_ramp';

const rate = await getRate();

# Response
{
  baseCurrency: string,
  targetCurrency: string,
  rate: number
}
```

### Get rate with amount

```bash
import { getRate } from 'paj_ramp';

const rate = await getRate(50000);

# Response
{
  rate: {
    baseCurrency: string,
    targetCurrency: string,
    rate: number
  },
  amounts: {
    userTax: number,
    merchantTax": number,
    amountUSD": number,
    userAmountFiat": number
   }
}
```

### Initiate Session

```bash
import { initiate } from 'paj_ramp';

const initialized = await initiate('your_email@gmail.com');

# Response
{
  email: string
}
```

### Verify Session

```bash
import { verify } from 'paj_ramp';

const verified = await verify('your_email@gmail.com', '1234', 'device signature');

# Response
{
  email: string,
  isActive: string,
  expiresAt: string,
  token: string
}
```

### Get Banks: Get list of banks

```bash
import { getBanks } from 'paj_ramp';

const banks = await getBanks();

# Response
[
  {
    id: string,
    name: string,
    country: string
  }
]
```

### Resolve Bank Account

```bash
import { resolveBankAccount } from 'paj_ramp';

const resolvedBankAccount = await resolveBankAccount('bank id', 'account number');

# Response
{
  accountName: string,
  accountNumber: string,
  bank: {
  id: string,
    name: string,
    code: string,
    country: string,
  }
}
```

### Add Bank Account

```bash
import { addBankAccount } from 'paj_ramp';

const addedBankAccount = await addBankAccount('token', 'bank id', 'account number');

# Response
{
  id: string,
  accountName: string,
  accountNumber: string,
  bank: string
}
```

### Get Bank Accounts

```bash
import { getBankAccounts } from 'paj_ramp';

const addedBankAccount = await getBankAccounts('token');

# Response
[
  {
    id: string,
    accountName: string,
    accountNumber: string,
    bank: string
  }
]
```

### Get Wallet Info

```bash
import { getWallet } from 'paj_ramp';

const wallet = await getWallet('wallet public key');

# Response
{
  id: string,
  publicKey: string,
  bankAccount: {
    id: string,
    accountName: string,
    accountNumber: string,
    bank: string
  }
}
```

### Add Wallet

```bash
import { addWallet } from 'paj_ramp';

const addedWallet = await addWallet('token', 'bank account id', 'secret key');

# Response
{
  id: string,
  publicKey: string,
  bankAccount: {
    id: string,
    accountName: string,
    accountNumber: string,
    bank: string
  }
}
```

### Switch Bank Account on Wallet

```bash
import { switchWalletBankAccount } from 'paj_ramp';

const switchedWallet = await switchWalletBankAccount('token','bank account id to switch to', 'wallet id', 'secret key');

# Response
{
  id: string,
  publicKey: string,
  bankAccount: {
    id: string,
    accountName: string,
    accountNumber: string,
    bank: string
  }
}
```

---

## 🧑‍💻 Author

Your Name — Gospel Chidiebube Chukwu


