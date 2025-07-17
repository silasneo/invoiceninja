# SupplyVest v1 Development Plan

---

## 📖 Overview

SupplyVest is a global invoicing and finance web application for small businesses operating in both USD (via USDC) and their local currency.  
It is built on top of Invoice Ninja (self-hosted, Vue 2 frontend, Laravel backend), and integrates Circle API for USDC wallet/payments, Bridge.xyz for bank on/off-ramp, and includes Treasury, Finance, and AI-powered features for Pro users.

---

## 📝 Key Features

1. **Multi-Tenant Company Support**
   - Users manage multiple companies.
   - Each company has its own currency, tax rate, and bank account.
   - Role-based access (admin, finance, viewer) per company.

2. **Dual-Currency Invoicing**
   - Products/services priced in USD and local currency.
   - Invoices issued in either currency.
   - PDF adapts to payment method and currency.

3. **Simplified Payments**
   - Pay with USDC (Circle API, auto-reconciled)
   - Local bank transfer (manual confirmation)
   - Users set up local payment details during company setup.

4. **Expense Tracking**
   - Log expenses in USD/local.
   - Auto-categorize and apply exchange rate.
   - Store notes, VAT, and receipt uploads.

5. **Dashboard & Reporting**
   - Filter and display data by currency.
   - Generate reports in USD, local, or both.
   - Dashboard shows wallet balance, income, expenses.

6. **Treasury (Pro)**
   - On-ramp local currency to USDC (Bridge.xyz).
   - Allocate USDC to yield vaults.
   - Monitor and withdraw yield earnings.

7. **Finance (Pro)**
   - Use USDC transaction history for credit scoring.
   - Offer working capital/BNPL in USDC.
   - Automate repayment from future inflows.

8. **AI-Powered Pro Features**
   - Chat-to-invoice (plain language to invoice).
   - Smart expense logging (AI receipt extraction).
   - Reporting assistant (natural language queries).
   - Follow-up helper (reminders, recurring clients).

9. **Monetization Strategy**
   - Free: invoicing, payments, basic reporting.
   - Pro: $35/month for Treasury, Finance, AI.
   - Fee waived for high USDC volume.
   - Optional USDC payment for Pro.

10. **Tech Stack**
    - Frontend: Vue 2 (extend Invoice Ninja UI)
    - Backend: Laravel (Invoice Ninja API)
    - Integrations: Circle API, Bridge.xyz, OpenAI API, Fixer.io/Circle FX

---

## 🚀 Launch Markets

- Initial focus: Nigeria, Kenya, India.

---

## 🔨 Implementation Steps & Order

### 1. Multi-Company Management
- Extend Vue UI and backend to support creation, listing, and switching between multiple companies.
- Add/confirm REST API endpoints for company CRUD.
- Store user roles per company.

### 2. USDC Wallet Provisioning
- Update DB structure (`companies` table) for USDC wallet/account fields.
- On company creation, provision USDC wallet via Circle API.
- Store wallet/account info in DB.

### 3. Role Management
- Implement/extend user role assignment per company.
- Enforce role-based access in backend and frontend.

### 4. Dual-Currency Invoice Flow
- Update invoice creation UI for USD/local currency selection.
- Store pricing per currency in invoice/products.
- Adapt invoice PDF/templates based on payment method/currency.

### 5. USDC Payment Integration
- Add USDC payment option to payment gateways (Circle API).
- Auto-reconcile USDC payments.
- Manual bank transfer option.

### 6. Expense Logging & AI
- Add expense logging UI for both currencies.
- Integrate receipt upload and notes.
- (Pro) Add AI categorization endpoint.

### 7. Dashboard & Reporting
- Show wallet balance, income, expenses in dashboard.
- Add currency-filtered reporting.

### 8. Treasury & Finance Modules (Pro)
- Integrate Bridge.xyz for on/off-ramp.
- Add yield vault allocation/monitoring.
- Implement credit/BNPL flows using USDC payment history.

### 9. AI Features (Pro)
- Integrate OpenAI API for chat-to-invoice, smart expense, reporting assistant, and follow-up helper.

---

## 📂 Database Changes Example

```php
// Migration: Add USDC wallet/account fields to companies table
Schema::table('companies', function (Blueprint $table) {
    $table->string('usdc_wallet_address')->nullable();
    $table->string('usdc_wallet_id')->nullable();
    $table->string('circle_account_id')->nullable();
    $table->string('usdc_wallet_status')->default('pending');
});
```

---

## 🧑‍💻 Developer Notes

- Use this file as a living document for planning, status, and Copilot reference.
- Update sections and action steps as the project evolves.
- Reference this file in Copilot Chat for context-aware code generation and Q&A.

---