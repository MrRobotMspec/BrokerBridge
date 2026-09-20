# BrokerBridge

A digital workspace connecting insurance brokers with insurance institutions.

---

## 📋 Overview

**BrokerBridge** is a front-end web application built as a single-page HTML file. It provides insurance brokers with a centralised workspace to manage clients, applications, quotes, documents, tasks, and reports, while also allowing them to browse insurance institutions and their available products.

The application is fully self-contained in one `index.html` file, including all styling (CSS) and logic (JavaScript). No external libraries, frameworks, or build tools are required.

---

## ✨ Features

### 🔐 Authentication
- Simple login screen with email and password fields.
- Session persistence via `localStorage` (login state is remembered on reload).
- Logout functionality that clears the session.

### 🧭 Navigation
- Collapsible sidebar with grouped navigation sections:
  - **Workspace** – Dashboard, Clients, Quotes & Applications
  - **Insurance** – Institutions, Products
  - **Management** – Documents, Tasks, Reports
  - **Resources** – Resources, Settings, Help & Support
- Responsive mobile menu (hamburger icon) for smaller screens.
- Sticky top bar with global search and notifications indicator.

### 📊 Dashboard
- Five KPI cards: Active Clients, Open Applications, Pending Quotes, Completed, Tasks Due.
- Applications overview bar chart (last 6 months).
- "Action Required" panel and "Recent Activity" feed.

### 👥 Clients
- Client portfolio table with search.
- Columns: Client, Type, Contact, Products, Status, Last Activity.
- Status badges (Active, New, Review).

### 📄 Quotes & Applications
- Application pipeline table with reference numbers (e.g., `BB-10025`).
- Tracks institution, product, date, and status (Submitted, Quote Received, Information Required).

### 🏢 Insurance Institutions
- Grid of insurance providers (Old Mutual, Santam, Hollard, Discovery Insure, Momentum Insure, Guardrisk).
- Each card shows a logo placeholder, description, and product tags.

### 📦 Insurance Products
- Product catalogue with institution, feature list, and "View Product" action.

### 📁 Documents
- Centralised document repository table (Verified / Review statuses).

### ✅ Tasks
- Task list with priority badges (High, Medium, Normal) and checkboxes.

### 📈 Reports
- Summary KPIs and a monthly applications bar chart.

### 📚 Resources & Support
- Quick-access cards for Broker Guides, Institution Portals, Training, FAQ, Contact Support, and Report a Problem.

### ⚙️ Settings
- Broker profile form (name, email, brokerage).

---

## 🛠️ Tech Stack

| Technology | Purpose |
|------------|---------|
| HTML5      | Structure & semantic markup |
| CSS3       | Styling, layout, responsive design |
| JavaScript (Vanilla) | Interactivity, page routing, session handling |

No dependencies. No build step.

---

## 📁 File Structure
