# 🧠 AI-Powered POS System with Odoo + Next.js

This is a modular, multi-tenant Point-of-Sale (POS) system that uses **Odoo** as the backend ERP and **Next.js 15 App Router** as the frontend UI framework. It also includes an AI assistant powered by **OpenRouter** (GPT/Claude/Mistral) to help shop owners make financial decisions, manage products, and generate social media content.

---

## 🚀 Tech Stack

| Layer             | Tech                     | Purpose                                         |
|------------------|--------------------------|-------------------------------------------------|
| Backend (ERP)     | [Odoo](https://www.odoo.com/) | Business logic, product, sales, inventory       |
| Frontend          | [Next.js 15 (App Router)](https://nextjs.org/) | POS UI, dashboards, reports                     |
| AI Assistant      | [OpenRouter.ai](https://openrouter.ai/) | Pricing advice, financial tips, content AI      |
| API Integration   | XML-RPC or REST (via Odoo) | Communicates with Odoo backend                  |
| Auth              | Auth.js or Clerk (optional) | Multi-tenant and secure access                 |
| UI Styling        | Tailwind CSS             | Modern responsive interface                     |
| Database (Odoo)   | PostgreSQL               | Managed by Odoo                                 |

---

## 📦 Features

### ✅ POS Core Features
- Multi-shop (multi-tenant) structure
- Fetch products and sales from Odoo
- Submit new sales orders from frontend
- View daily and monthly sales reports
- Custom roles: `owner`, `cashier`, `manager`

### 🧠 AI Features
- Chat assistant for business decisions
- Price suggestion based on product data
- Generate social media captions and hashtags
- Upload videos (YouTube/Instagram ready)

---

## 🗂️ Folder Structure (Frontend)

```

/app/
├── dashboard/          # All core POS modules
│   ├── products/        → Product list
│   ├── sales/           → POS terminal
│   ├── reports/         → Financial reports
│   └── ai-assistant/    → AI chat & tools
├── api/                # API routes calling Odoo or AI
│   └── openrouter/
└── layout.tsx          # App shell

/lib/
├── odoo.ts             → Odoo API helpers (XML-RPC or REST)
├── openrouter.ts       → OpenRouter fetch logic

/components/
├── ProductList.tsx
├── POSCart.tsx
├── ReportCard.tsx
└── AssistantChat.tsx

````

---

## 🔌 API Connection

This app connects to **Odoo** using either:

### Option 1: XML-RPC (Native Odoo)
> Make sure Odoo is accessible on port 8069 with external API enabled.

```ts
await callOdoo('product.product', 'search_read', [[['sale_ok', '=', true]]])
````

### Option 2: Odoo REST API (3rd-party module required)

> Install a module like `odoo-rest-api` for easier JSON responses.

```ts
GET https://your-odoo.com/api/products
Authorization: Bearer <token>
```

---

## 🧠 OpenRouter AI

Used to generate:

* Business suggestions
* Pricing guidance
* Captions for social media

```ts
POST https://openrouter.ai/api/v1/chat/completions
Authorization: Bearer <OPENROUTER_API_KEY>
```

---

## ⚙️ Setup Instructions

### 1. Clone this repository

```bash
git clone https://github.com/your-org/ai-pos-nextjs-odoo.git
cd ai-pos-nextjs-odoo
```

### 2. Setup Environment Variables

Create `.env` and add:

```env
ODOO_URL=http://localhost:8069
ODOO_DB=your_db
ODOO_USER=admin
ODOO_PASSWORD=admin

OPENROUTER_API_KEY=your_openrouter_key
```

### 3. Install Dependencies

```bash
npm install
```

### 4. Run Dev Server

```bash
npm run dev
```

---

## 🔐 Auth & Multi-Tenant Support

* Each user belongs to a `shop`
* Middleware detects shop ID and loads related data
* Role-based access (cashier, owner, etc.)

---

## 🛣️ Roadmap

| Feature                     | Status        |
| --------------------------- | ------------- |
| Connect to Odoo via XML-RPC | ✅ Done        |
| Product Management          | ✅ Done        |
| Sales Order Submission      | ✅ Done        |
| AI Assistant Integration    | ✅ In Progress |
| Video Upload for Social     | 🔜 Planned    |
| Multi-Tenant Shop Context   | ✅ In Progress |

---

## 🧑‍💻 Contributions

PRs are welcome! Please follow the modular folder structure and prefer **server actions** over client mutators where possible.

---

## 🪪 License

MIT — Free for commercial and personal use.

---

## ✨ Credits

* [Odoo ERP](https://www.odoo.com/)
* [Next.js](https://nextjs.org/)
* [OpenRouter.ai](https://openrouter.ai/)
* [Tailwind CSS](https://tailwindcss.com/)

---
