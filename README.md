# Auto Store Manager

### AI-Driven Supply Chain Risk Monitoring and Automated Inventory Replenishment

Auto Store Manager is a full-stack application for small and medium retail businesses (for example, kirana stores) to:

* monitor supplier risk in near real-time
* manage in-store inventory
* integrate billing outputs (manual/API/CSV)
* automatically place supply orders to the best-price supplier when stock goes below threshold

---

## Project Demo

[Watch Demo Video](https://www.youtube.com/watch?v=vFpC7oJ-Gpo)

---

## What Problem This Solves

In real stores, stock-outs and supplier uncertainty cause lost sales and operational stress.
Auto Store Manager solves this by combining:

1. Risk intelligence (news/weather-driven supplier risk signals)
2. Inventory visibility (what is currently in stock)
3. Automated replenishment (threshold-based ordering)
4. Supplier optimization (best-price supplier selection)

This reduces manual tracking, avoids emergency procurement, and improves supply continuity.

---

## Key Features

### Authentication & Access

* Register/Login with JWT authentication
* Protected routes for dashboard modules

### Supplier Registry

* Add/manage suppliers with location and category
* Store supplier email and phone for real notifications
* Per-supplier:

  * active/inactive status
  * auto-order enable/disable
  * configurable baseline pricing

### Risk Intelligence Pipeline

* Scheduled ingestion, classification, and scoring pipeline
* Manual pipeline trigger from UI
* Risk levels (low, medium, high) per supplier
* Alerts generated and listed in Alerts page

### Inventory Management

* Store profile (shop name/type)
* Add products with category, quantity, unit
* Search inventory
* Manual bill-out (sale) to decrement stock

### Billing Integration

* External billing machine/API token integration
* Secure machine token generation
* CSV import fallback (product_name, quantity_sold)
* Manual sync endpoint

### Auto Replenishment

* Global auto-order ON/OFF
* Per-product threshold quantity
* Auto-order workflow:

  1. Detect low stock
  2. Generate alert
  3. Select best-price supplier
  4. Create supply order
  5. Notify supplier via email

### Supplier Product Matching

* Exact product-level supplier catalog
* Supplier selection based on price and availability

### UI Features

* Responsive dashboard
* Dark/Light theme toggle
* Improved readability for forms and inputs

---

## Tech Stack

### Frontend

* React
* Vite
* React Router
* Axios
* Recharts / Framer Motion

### Backend

* FastAPI
* SQLAlchemy
* APScheduler
* JWT authentication
* bcrypt password hashing

### AI / NLP

* Hugging Face Transformers
* Zero-shot classification (facebook/bart-large-mnli)
* Rule + keyword assisted classification

### Database

* MySQL

### External APIs

* NewsAPI
* OpenWeather API

### Notifications

* SMTP Email Integration

---

## Project Structure

```text
backend/
  app/
    models/
    routes/
    pipeline/
    services/

frontend/
  src/
    pages/
    components/

database/
  schema.sql
```

---

## Database Notes

Important tables include:

* users
* suppliers
* raw_events, classified_risks, supplier_risk_scores, alerts
* inventory_products, billing_integrations
* supply_orders
* supplier_product_catalog

---

## Setup and Run

### Backend

```bash
cd backend
venv\Scripts\activate
uvicorn app.main:app --reload
```

### Frontend

```bash
cd frontend
npm install
npm run dev
```

---

## Environment Variables

Create a `.env` file in backend:

```env
DB_HOST=localhost
DB_PORT=3306
DB_USER=your_user
DB_PASSWORD=your_password
DB_NAME=watchtower

NEWSAPI_KEY=your_key
OPENWEATHER_KEY=your_key

SMTP_HOST=your_host
SMTP_USER=your_email
SMTP_PASSWORD=your_password
```

---

## Core Workflow

1. Owner manages suppliers and product catalog
2. Billing updates inventory
3. System monitors stock thresholds
4. If stock is low:

   * alert is generated
   * best supplier is selected
   * order is created and logged
5. Alerts and order history are visible in dashboard

---

## Future Enhancements

* Supplier-side order acknowledgment
* Purchase order PDF generation
* Product name matching improvements
* Multi-branch inventory support
* Demand forecasting

---

## Team

Lakshay Kumar
Deepak Kumar Bind
Puneet Kumar
Shiv Yadav Shalhata

Noida Institute of Engineering and Technology (NIET), Greater Noida
