# 🚜 AgriRent Marketplace (Smart IoT & Escrow Rental Platform)

An advanced, high-trust Full-Stack (MERN) marketplace designed for seamless agricultural equipment rentals. Unlike traditional rental platforms, **AgriRent** solves real-world trust deficits between farmers and asset owners by integrating a **Simulated IoT Asset Activation System** and a secure **Smart Escrow Financial Workflow**.

---

## 💡 The Problem & Our Unique Solution (X-Factor)

### The Core Problem in Agri-Rentals:
1. **Owners fear equipment damage/theft:** They worry renters will overuse or mistreat expensive machinery.
2. **Farmers fear financial fraud:** They worry about paying upfront only to receive faulty, malfunctioning equipment.

### Our Solution:
*   **Smart Escrow Wallet:** When a farmer books an item, the funds are securely held by the platform's Escrow system (`HELD_IN_ESCROW`). Funds are only released to the vendor after successful confirmation of the job or automated usage tracking verification.
*   **Simulated IoT Switch (Pay-Per-Hour):** Equipment is locked out-of-the-box. Upon arrival, the farmer uses a secure 6-digit dynamic activation key via the app to "Unlock/Start" the tractor. The system tracks the precise minutes used, transitioning from flat daily rates to a fair, usage-based pricing engine.

---

## 🛠️ Tech Stack & Architecture

- **Frontend:** React.js, Tailwind CSS, Context API / Zustand, React Router Dom
- **Backend:** Node.js, Express.js, JWT (HTTP-only cookies), Socket.io (for real-time dispute alerts)
- **Database:** MongoDB (Mongoose), featuring geospatial queries (`$geoNear`) for finding nearby tools.

[ React.js / Tailwind CSS Frontend ]
│
HTTP/REST   │   WebSockets (Live Lock Status)
┌──────────────┴──────────────┐
▼                             ▼
┌──────────────────────────────────────────────┐
│          Node.js / Express.js Backend        │
└──────────────────────┬───────────────────────┘
▼
┌───────────────────────────┐
│     MongoDB Database      │
└───────────────────────────┘

---

## 📂 Project Structure

```text
agrirent-marketplace/
│
├── backend/                  # Node.js + Express Server
│   ├── config/               # DB connection configurations
│   ├── controllers/          # Business logic (Auth, Escrow Engine, IoT Validation)
│   ├── models/               # Schemas (User.js, Equipment.js, Booking.js)
│   ├── routes/               # API Router setup (/api/v1/...)
│   └── server.js             # Entry point
│
└── frontend/                 # React UI Client
    ├── src/
    │   ├── components/       # Reusable blocks (Navbar, MapView, Timer)
    │   ├── pages/            # Dashboard, EscrowPanel, AssetDetails
    │   └── App.jsx
```

---

## 🚀 Key Features Built

- [ ] **Dual-Role Authentication:** Separate dynamic workflows for Farmers (Renters) and Vendors (Owners) protected by secure JWTs.
- [ ] **Geospatial Proximity Search:** Find available equipment within a 10km to 50km radius using MongoDB Location Indexes.
- [ ] **Smart Escrow State-Machine:** Manages payment lifecycles through states: `HELD_IN_ESCROW`, `RELEASED`, `DISPUTED`, `REFUNDED`.
- [ ] **IoT Dynamic Activation:** Generate unique short-lived tokens to simulate physical activation logs on heavy machinery.

---

## 💻 Getting Started Locally

### Prerequisites
- Node.js (v18+ recommended)
- MongoDB Atlas Account or Local MongoDB Community Server

### Setup Steps

1. **Clone the repository:**
   ```bash
   git clone https://github.com
   cd agrirent-marketplace
   ```

2. **Configure Environment Variables:**
   Create a `.env` file inside the `backend` directory:
   ```env
   PORT=5000
   MONGO_URI=your_mongodb_connection_string
   JWT_SECRET=your_super_secure_jwt_secret
   ```

3. **Install Backend Dependencies & Run:**
   ```bash
   cd backend
   npm install
   npm run dev
   ```

4. **Install Frontend Dependencies & Run:**
   ```bash
   cd ../frontend
   npm install
   npm run dev
   ```

---
 *"I engineered a high-trust agri-rental platform resolving peer-to-peer security issues. I implemented an advanced Escrow pattern using MongoDB transaction checkpoints to lock down payments safely until IoT simulation signals validated successful equipment delivery. This completely removes the friction of upfront payment frauds in rural setups."*



