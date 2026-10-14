<h1 align="center">🛒 SuperShop Management — React Frontend</h1>

<p align="center">
  <b>A modern, enterprise-grade ERP frontend for Supply Chain & Inventory Management</b><br/>
  Built with React 18 · TypeScript · Vite · Tailwind CSS
</p>

<p align="center">
  <img src="https://img.shields.io/badge/React%2018-61DAFB?style=flat-square&logo=react&logoColor=black" />
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white" />
  <img src="https://img.shields.io/badge/Vite-646CFF?style=flat-square&logo=vite&logoColor=white" />
  <img src="https://img.shields.io/badge/Tailwind%20CSS-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white" />
  <img src="https://img.shields.io/badge/React%20Router-CA4245?style=flat-square&logo=reactrouter&logoColor=white" />
  <img src="https://img.shields.io/badge/Axios-5A29E4?style=flat-square&logo=axios&logoColor=white" />
</p>

---

## 📖 About

A complete Supply Chain ERP frontend that consumes the SupplyChain ERP Core API. It automates the full procurement-to-receipt cycle — from employee requisition to GRN approval — with role-based dashboards, warehouse location setup, and inventory tracking.

## ✨ Features

- 🔐 **JWT Authentication** — login, register, auto-logout after inactivity
- 🎭 **Role-Based Dashboards** — Employee · Dept Head · Purchase · Store · Admin
- 📝 **Employee Requisition** — create, submit, revise, track lifecycle
- 🛒 **Procurement Workflow** — PR → RFQ → Quotation → CS → PO
- 📦 **Store Operations** — pending queue, FIFO issue, forward to purchase
- 🏭 **GRN & QC** — goods receipt with batch/expiry tracking
- 🌳 **Warehouse Setup** — 7-level hierarchy (Warehouse → Bin)
- 📊 **Dashboard Analytics** — KPIs, stats, activity feeds
- 🖨️ **Print Templates** — A4-ready PO, GRN, PR invoices
- 🎨 **Universal Design System** — reusable form components

---

## 🚀 Quick Start

### 1️⃣ Clone

```bash
git clone https://github.com/TahminaKhanNipa10-Codes/supershop-management.git
cd supershop-management
```

### 2️⃣ Install Packages

```bash
npm install
```

### 3️⃣ Configure `.env.development`

```env
VITE_API_BASE_URL=http://localhost:5186
```

> ⚠️ Replace with your backend API URL. For production, use `.env.production`.

### 4️⃣ Run the App

```bash
npm run dev
```

🌐 **App** → `http://localhost:3000`

### 5️⃣ Build for Production

```bash
npm run build
```

Production-ready files will be in `dist/`.

---

## 🔐 Default Login

| Email | Password |
| :--- | :--- |
| `admin@supershop.com` | `Admin@123` |

> ⚠️ Change the default admin password after first login.

---

## 📜 Available Scripts

| Command | Description |
| :--- | :--- |
| `npm run dev` | Start development server |
| `npm run build` | Build for production |
| `npm run preview` | Preview production build locally |

---

## 📡 API Endpoints Used

### 🔐 Authentication

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `POST` | `/api/Auth/register` | Register new user |
| `POST` | `/api/Auth/login` | Login & get JWT |
| `GET` | `/api/Auth/me` | Get current user |

### 📦 Master Data

- `/api/ItemCategory` — Item categories
- `/api/SubCategory` — Sub-categories
- `/api/Brand` — Brands
- `/api/Unit` — Units
- `/api/UnitSet` — Unit sets
- `/api/Currency` — Currencies
- `/api/Department` — Departments
- `/api/Supplier` — Suppliers
- `/api/Product` — Products

### 🛒 Procurement Workflow

- `GET/POST` — `/api/requisitions`
- `PATCH` — `/api/requisitions/{id}/submit`
- `PATCH` — `/api/requisitions/{id}/approve`
- `POST` — `/api/store/issue`
- `POST` — `/api/store/forward-to-purchase`
- `GET/POST` — `/api/PurchaseRequisition`
- `GET/POST` — `/api/RequestForQuotation`
- `GET/POST` — `/api/SupplierQuotation`
- `GET/POST` — `/api/ComparativeStatement`
- `GET/POST` — `/api/PurchaseOrder`
- `GET/POST` — `/api/GRN`

### 🏭 Inventory & Location

- `GET` — `/api/Inventory`
- `GET` — `/api/Inventory/low-stock`
- `GET/POST` — `/api/StockMovement`
- `GET` — `/api/location/tree`
- `GET` — `/api/location/dropdowns`
- `GET/POST` — `/api/location/warehouses`
- `GET/POST` — `/api/location/floors`
- `GET/POST` — `/api/location/zones`
- `GET/POST` — `/api/location/aisles`
- `GET/POST` — `/api/location/racks`
- `GET/POST` — `/api/location/shelfs`
- `GET/POST` — `/api/location/bins`

### 🧑‍💼 Admin & Dashboard

- `GET/POST` — `/api/Admin/roles`
- `GET/PUT` — `/api/Admin/roles/{role}/permissions`
- `GET` — `/api/Admin/users`
- `PUT` — `/api/Admin/users/{id}/roles`
- `GET` — `/api/Dashboard/stats`

---

## 📁 Project Structure

```text
supershop-management/
├── public/                  → Static assets (logo, video)
├── src/
│   ├── api/                 → Axios API clients
│   ├── components/
│   │   ├── common/          → ProtectedRoute, InactivityWarning
│   │   ├── form/            → Universal design system
│   │   ├── layout/          → DashboardLayout, Sidebar
│   │   ├── requisitions/    → Requisition components
│   │   └── store/           → IssueProductModal
│   ├── context/             → AuthContext
│   ├── hooks/               → useAutoLogout, useScrollIndicator
│   ├── pages/
│   │   ├── auth/            → LoginPage, RegisterPage
│   │   ├── dashboard/       → 30+ dashboard pages
│   │   ├── LandingPage.tsx
│   │   └── UnauthorizedPage.tsx
│   ├── styles/              → Global & feature CSS
│   ├── types/               → Shared TypeScript interfaces
│   ├── App.tsx              → Route definitions
│   ├── main.tsx             → App entry point
│   └── vite-env.d.ts
├── .env.development
├── .env.production
├── index.html
├── package.json
├── postcss.config.js
├── tailwind.config.js
├── tsconfig.json
├── tsconfig.node.json
├── vercel.json
├── vite.config.ts
├── screenshots/                     → README images
│   ├── login.jpeg
│   ├── dashboard.jpeg
│   ├── requisition.jpeg
│   ├── report.jpeg
│   ├── purchase-order.jpeg
│   ├── comparative-statement.jpeg
│   └── grn.jpeg
└──
```

---

📸 Screenshots
🔐 Login Page & 📊 Dashboard

<p align="center"> <img src="screenshots/login.jpeg" width="48%"> <img src="screenshots/dashboard.jpeg" width="48%"> </p>
📝 Employee Requisition & 📈 Report

<p align="center"> <img src="screenshots/requisition.jpeg" width="48%"> <img src="screenshots/report.jpeg" width="48%"> </p>
🛒 Purchase Order & 📋 Comparative Statement

<p align="center"> <img src="screenshots/purchase-order.jpeg" width="48%"> <img src="screenshots/comparative-statement.jpeg" width="48%"> </p>
🏭 GRN — Goods Receipt with QC

<p align="center"> <img src="screenshots/grn.jpeg" width="95%"> </p>
---

## 🎨 Design System

The project includes a universal form design system under `src/components/form/`:

| Component | Purpose |
| :--- | :--- |
| `StatsHeader` | Colored header with KPI chips |
| `FormSection` | Card wrapper with title + body |
| `FieldGroup` | Label + input wrapper |
| `Input` / `Select` / `Textarea` / `Toggle` | Form controls |
| `DynamicTable` | Editable table with add/remove rows |
| `ViewSection` / `ViewField` | Read-only label:value grid |
| `StatusBanner` | Colored status banner |
| `FilterBar` / `FilterField` | Search/filter row |
| `FormActions` / `ActionButton` | Bottom action buttons |
| `Badge` | Status chips |
| `COLORS` | Module color palette |

---

## 🔑 Roles & Permissions

**Roles:** Admin, Manager, User, Employee, PurchaseOfficer, PurchaseManager, StoreManager, WarehouseManager, DepartmentHead, MD

Access control is enforced via:

- `<ProtectedRoute roles={[...]}>` — role-based route guard
- `hasRole('Admin')` / `hasPermission('requisition:approve')` — component-level checks


---

## 👩‍💻 Connect With Me

<p align="center">
  <a href="https://github.com/TahminaKhanNipa10-Codes">
    <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" />
  </a>
  <a href="https://linkedin.com/in/your-profile">
    <img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" />
  </a>
  <a href="mailto:your.email@example.com">
    <img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" />
  </a>
</p>

<p align="center">
  <b>⭐ If you find this project useful, give it a star! ⭐</b><br/>
  <sub>MIT License © 2026 Tahmina Khan Nipa</sub>
</p>
