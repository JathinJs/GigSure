# 🛵 GigSure

## Ensuring income stability for gig workers

Built for **Guidewire DEVTrails 2026 Hackathon**

GigShield is an **AI-powered parametric insurance platform** that protects gig workers from **income loss caused by uncontrollable external disruptions** such as heavy rain, extreme heat, pollution, floods, and curfews.

Instead of manual claim filing, GigShield **automatically detects disruptions and triggers instant payouts**.

---

# 📌 Problem Statement

Delivery partners working on platforms like:

* Zomato
* Swiggy

are highly vulnerable to external disruptions.

These include:

* Heavy rain
* Extreme heat
* Severe pollution
* Floods
* Local strikes or curfews

During such events, delivery partners **cannot work outdoors**, leading to **loss of daily wages**.

Studies show gig workers can lose **20–30% of their monthly income** due to these disruptions.

⚠️ **Coverage Scope:**
GigShield only covers **income loss**, not:

* health insurance
* life insurance
* accidents
* vehicle repair

---

# 👤 Persona

**Name:** Rahul
**Age:** 26
**Profession:** Food Delivery Partner
**Platform:** Zomato / Swiggy
**City:** Hyderabad

Rahul works **8 hours per day** and earns about **₹800–₹1200 daily**.

Because he is paid per delivery, **any disruption immediately reduces his income**.

---

# 📖 Scenario Examples

### Scenario 1 — Heavy Rain

Heavy rainfall hits Hyderabad (>70mm/hr).

Rahul cannot safely ride his bike.

GigShield detects rainfall data via Weather API and automatically credits **₹350 compensation**.

---

### Scenario 2 — Extreme Heat

Temperature reaches **45°C** in Hyderabad.

Authorities issue a heat advisory.

GigShield detects the event and compensates workers for unsafe working hours.

---

### Scenario 3 — Curfew or Strike

A sudden local strike blocks restaurant pickup zones.

GigShield detects the disruption through civic alerts and automatically triggers payouts.

---

### Scenario 4 — Severe Air Pollution

AQI crosses **400 (Severe category)** in Rahul's zone.

GigShield cross-validates AQI data with his GPS inactivity and triggers income compensation for lost hours.

---

# ⚙️ Application Workflow

```
Worker Registration
        ↓
Zone Risk Profiling (AI)
        ↓
Weekly Policy Purchase
        ↓
Real-Time Event Monitoring
        ↓
Parametric Trigger Detected
        ↓
Automatic Claim Processing
        ↓
Instant Payout via UPI
```

Workers **never need to manually file a claim**.

---

# 💰 Weekly Premium Model

Gig workers operate on **weekly earnings cycles**, so GigShield uses **weekly insurance pricing**.

| Tier     | Weekly Premium | Coverage Limit | Daily Payout |
| -------- | -------------- | -------------- | ------------ |
| Basic    | ₹29            | ₹1,000         | ₹200         |
| Standard | ₹59            | ₹2,500         | ₹450         |
| Pro      | ₹99            | ₹5,000         | ₹800         |

---

## Dynamic Premium Adjustment

Premium is adjusted using AI risk scoring.

Factors considered:

* Worker delivery zone risk
* Weather forecast risk
* Historical claim frequency
* Pollution levels

Formula:

```
Final Premium =
Base Tier Price
+ Zone Risk Adjustment
+ Forecast Risk Adjustment
- Safe Zone Discount
```

---

# ⚡ Parametric Triggers

Claims trigger automatically when verified events occur.

| Trigger          | Data Source  | Condition              |
| ---------------- | ------------ | ---------------------- |
| Heavy Rain       | Weather API  | Rainfall > 60mm/hr     |
| Extreme Heat     | Weather API  | Temperature > 43°C     |
| Severe Pollution | AQI API      | AQI > 350              |
| Flood Alert      | Civic Alerts | Flood warning issued   |
| Curfew / Strike  | Civic API    | Zone closure > 2 hrs   |

Claims trigger only if:

```
External Event Detected
AND
Worker Inactivity Verified
```

---

# 📱 Platform Choice

GigShield is built as a **Web Application with Progressive Web App (PWA) support**.

Reasons:

* Delivery workers already use multiple mobile apps
* PWA provides **mobile-like experience without app store approval**
* Faster development during hackathon
* Web interface supports **both workers and admin dashboards**
* Built with **Next.js + React** for fast, responsive UI across all screen sizes

Workers can **install the PWA on their phone** for quick access.

---

# 🤖 AI / ML Integration

GigShield uses AI to improve pricing accuracy and detect fraud.

### Risk Profiling

Workers are grouped into risk categories using:

Model: **K-Means Clustering**

Factors:

* city risk level
* rainfall frequency
* pollution levels
* claim history

---

### Dynamic Premium Prediction

Model: **Gradient Boosting Regressor**

Used to calculate dynamic weekly premiums.

---

### Fraud Detection

Model: **Isolation Forest**

Detects anomalies such as:

* GPS spoofing
* duplicate claims
* abnormal claim frequency

---

### Claim Forecasting

Model: **Prophet Time-Series Model**

Used in the admin dashboard to forecast expected claim volumes.

---

# 🧱 Tech Stack

### Frontend

* React / Next.js 14
* Tailwind CSS
* Zustand
* Recharts
* Leaflet Maps

---

### Backend

* Node.js
* Next.js API Routes
* PostgreSQL
* Supabase

---

### AI / ML

* Python
* FastAPI
* scikit-learn
* Prophet

---

### APIs

* OpenWeatherMap
* Central Pollution Control Board (CPCB)
* OpenAQ API
* Mock Civic Alert API

---

### Payments

* Razorpay sandbox

---

# 🗓 Development Plan

## Phase 1 — Ideation & Foundation (Mar 4–20)

* [x] Idea validation
* [x] Persona design
* [x] Workflow definition
* [x] Tech stack selection
* [ ] Initial GitHub repository setup
* [ ] Build worker onboarding flow (UI)
* [ ] Record 2-minute strategy video

---

## Phase 2 — Automation & Protection (Mar 21–Apr 4)

* [ ] Worker onboarding and registration flow
* [ ] Weekly premium calculator (dynamic)
* [ ] 5 automated parametric event triggers
* [ ] Basic claims automation
* [ ] Razorpay sandbox payout integration
* [ ] Record 2-minute demo video

---

## Phase 3 — Scale & Optimise (Apr 5–17)

* [ ] Fraud detection AI model (Isolation Forest)
* [ ] Worker dashboard (earnings protected, active coverage)
* [ ] Admin analytics dashboard (loss ratios, forecasts)
* [ ] End-to-end disruption simulation demo
* [ ] Final pitch deck (PDF)
* [ ] Record 5-minute walkthrough demo video

---

# 👥 Team

| Member   | Role                      |
| -------- | ------------------------- |
| Member 1 | Frontend / Full-Stack     |
| Member 2 | Backend / API Integration |
| Member 3 | AI / ML & Data Modelling  |
| Member 4 | UI / UX & Product         |

---

⭐ Built for **Guidewire DEVTrails 2026** — *Seed. Scale. Soar.*
