# 🏦 Pomelo Banking App

A modern, secure banking application built with Next.js 14, featuring real-time bank account aggregation, peer-to-peer money transfers, and comprehensive financial management tools.

## 🌟 Features

### Core Banking Features
- 🏦 **Multi-Bank Account Linking** - Connect multiple bank accounts via Plaid integration
- 💸 **P2P Money Transfers** - Send money to other users using Dwolla
- 📊 **Real-Time Transaction Tracking** - View all transactions across linked accounts
- 📈 **Financial Analytics** - Spending insights, category breakdowns, and budget tracking
- 🔐 **Secure Authentication** - Email/password authentication via Appwrite
- 📱 **Responsive Design** - Works seamlessly on desktop, tablet, and mobile

### Security Features
- ✅ All dependencies updated with security patches
- ✅ Next.js 14.2.33 (latest security fixes)
- ✅ 0 known vulnerabilities
- ✅ HTTP-only cookies for session management
- ✅ Secure data encryption in transit
- ✅ Environment-based configuration

## 🛠️ Tech Stack

### Frontend
- **Next.js 14.2.33** - React framework with App Router
- **TypeScript** - Type-safe code
- **Tailwind CSS** - Utility-first styling
- **shadcn/ui** - Beautiful UI components
- **React Hook Form** - Form management
- **Zod** - Schema validation
- **Chart.js** - Data visualization

### Backend & Services
- **Appwrite** - Database, authentication, and storage
- **Plaid** - Bank account connectivity and transaction data
- **Dwolla** - ACH payment processing
- **Sentry** - Error tracking and monitoring

## 📋 Prerequisites

Before running this application, you need accounts with:

1. **Appwrite** (Database & Auth)
   - Sign up: https://appwrite.io
   - Free tier available

2. **Plaid** (Bank Connections)
   - Sign up: https://dashboard.plaid.com/signup
   - Use sandbox mode for development (free)

3. **Dwolla** (Money Transfers)
   - Sign up: https://www.dwolla.com/
   - Use sandbox mode for development (free)

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/Mariosat15/Pomelo_Banking_app.git
cd Pomelo_Banking_app
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Set Up Environment Variables

Create a `.env` file in the root directory:

```env
# NEXT.JS
NEXT_PUBLIC_SITE_URL=http://localhost:3000

# APPWRITE
NEXT_PUBLIC_APPWRITE_ENDPOINT=https://cloud.appwrite.io/v1
NEXT_PUBLIC_APPWRITE_PROJECT=your_project_id
APPWRITE_DATABASE_ID=your_database_id
APPWRITE_USER_COLLECTION_ID=your_user_collection_id
APPWRITE_BANK_COLLECTION_ID=your_bank_collection_id
APPWRITE_TRANSACTION_COLLECTION_ID=your_transaction_collection_id
APPWRITE_SECRET=your_api_secret

# PLAID
PLAID_CLIENT_ID=your_plaid_client_id
PLAID_SECRET=your_plaid_secret
PLAID_ENV=sandbox
PLAID_PRODUCTS=auth,transactions,identity
PLAID_COUNTRY_CODES=US,CA

# DWOLLA
DWOLLA_KEY=your_dwolla_key
DWOLLA_SECRET=your_dwolla_secret
DWOLLA_BASE_URL=https://api-sandbox.dwolla.com
DWOLLA_ENV=sandbox
```

### 4. Set Up Appwrite

1. Create a new project in [Appwrite Console](https://cloud.appwrite.io/)
2. Create a database
3. Create three collections:
   - **Users** - Store user profiles
   - **Banks** - Store bank connections
   - **Transactions** - Store transaction history
4. Copy the IDs to your `.env` file

### 5. Run Development Server

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

### 6. Create Your First Account

1. Navigate to `/sign-up`
2. Fill in your information (use test data in sandbox mode)
3. For SSN, use test values like `123-45-6789` in sandbox
4. Sign in and start using the app!

## 📁 Project Structure

```
pomelo-banking-app/
├── app/                    # Next.js App Router
│   ├── (auth)/            # Authentication pages
│   │   ├── sign-in/
│   │   └── sign-up/
│   ├── (root)/            # Main application pages
│   │   ├── page.tsx       # Dashboard
│   │   ├── my-banks/      # Bank accounts page
│   │   ├── payment-transfer/  # Transfer money
│   │   └── transaction-history/  # Transaction list
│   └── layout.tsx
├── components/            # React components
│   ├── ui/               # shadcn/ui components
│   ├── AuthForm.tsx      # Authentication form
│   ├── BankCard.tsx      # Bank account card
│   ├── PlaidLink.tsx     # Plaid integration
│   └── ...
├── lib/                   # Utility functions
│   ├── actions/          # Server actions
│   │   ├── user.actions.ts
│   │   ├── bank.actions.ts
│   │   └── transaction.actions.ts
│   ├── appwrite.ts       # Appwrite client
│   ├── plaid.ts          # Plaid client
│   └── utils.ts          # Helper functions
├── types/                 # TypeScript type definitions
└── constants/            # App constants
```

## 🔐 Security Considerations

### Current Implementation
- ✅ Server-side rendering for sensitive operations
- ✅ HTTP-only cookies for session management
- ✅ Environment variables for secrets
- ✅ Dwolla handles KYC/AML compliance
- ✅ Plaid handles secure bank connections
- ✅ All dependencies patched and up-to-date

### For Production Deployment
Before deploying to production, implement:
- [ ] Multi-factor authentication (MFA)
- [ ] Rate limiting on authentication endpoints
- [ ] Enhanced password requirements
- [ ] Security headers (CSP, HSTS, etc.)
- [ ] Regular security audits
- [ ] Logging and monitoring
- [ ] Database backups
- [ ] SSL/TLS certificates

## ⚠️ Important Notes

### Sandbox vs Production

This app is configured for **sandbox/development mode** by default:
- Plaid uses test bank accounts
- Dwolla uses sandbox environment
- No real money is transferred
- Test credentials are safe to use

### Compliance & Licensing

**This application relies on regulated partners:**
- **Dwolla** is the licensed Money Services Business (MSB)
- **Plaid** handles secure bank connections
- Your app acts as a **technology platform** only

**You do NOT need:**
- ❌ Money Transmitter License (Dwolla has it)
- ❌ Banking license
- ❌ Your own KYC/AML program (Dwolla handles it)

**You DO need:**
- ✅ Terms of Service
- ✅ Privacy Policy
- ✅ Data security measures
- ✅ Fraud prevention

## 🚧 Roadmap

### Planned Features
- [ ] Virtual card issuance
- [ ] Budget management tools
- [ ] Bill tracking and reminders
- [ ] Financial insights dashboard
- [ ] Savings goals
- [ ] Investment account linking
- [ ] Credit score monitoring
- [ ] Multi-factor authentication
- [ ] Mobile app (React Native)

## 🐛 Known Issues

1. **"No session" error on first run**
   - **Cause:** No user account created yet
   - **Solution:** Sign up at `/sign-up` first

2. **Bank connection fails**
   - **Cause:** Missing Plaid credentials
   - **Solution:** Add `PLAID_CLIENT_ID` and `PLAID_SECRET` to `.env`

3. **Money transfer fails**
   - **Cause:** Missing Dwolla credentials
   - **Solution:** Add `DWOLLA_KEY` and `DWOLLA_SECRET` to `.env`

## 📚 Documentation

- [Next.js Docs](https://nextjs.org/docs)
- [Appwrite Docs](https://appwrite.io/docs)
- [Plaid Docs](https://plaid.com/docs/)
- [Dwolla Docs](https://developers.dwolla.com/)

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Original tutorial by [JavaScript Mastery](https://www.youtube.com/@javascriptmastery)
- Based on the [Horizon Banking](https://github.com/adrianhajdin/banking) tutorial
- Enhanced with security fixes and production-ready practices

## 📞 Support

For issues or questions:
- Open an issue on GitHub
- Check the [Discussions](https://github.com/Mariosat15/Pomelo_Banking_app/discussions) tab

---

**Built with ❤️ by Mariosat15**

**Status:** ✅ Ready for Development | 🔒 Security Patched | 🚀 Sandbox Ready

