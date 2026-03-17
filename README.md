# 🛵 GigSure

## AI-Powered Parametric Income Insurance for Delivery Partners

Built for **Guidewire DEVTrails 2026 Hackathon**

GigSure is an **AI-powered parametric insurance platform** that protects Zomato and Swiggy delivery partners from **income loss caused by uncontrollable external disruptions** — heavy rain, extreme heat, pollution, floods, and curfews.

Instead of manual claim filing, GigSure **automatically detects disruptions and triggers instant payouts via UPI.**

---

# 📌 Problem Statement

Delivery partners on Zomato and Swiggy earn only when they ride. They have no fixed salary, no sick leave, and no employer. Any external disruption that stops them from working means zero income for that day.

**The real impact:**

* Hyderabad averages 14 significant rain disruption days per year
* Delhi has 22+ hazardous AQI days annually
* A single disruption day costs a delivery partner ₹800–₹1,400
* Workers lose **20–30% of monthly income** due to disruptions
* No insurance product in India was ever designed to cover this gap

**Meet Rahul:**

Rahul is 26. He delivers for Zomato in Banjara Hills, Hyderabad. He works 8 hours a day and earns around ₹950 on a good day. He pays ₹4,500 rent every month and sends money home. When it rains heavily, he cannot ride. He loses the entire day. No one compensates him.

GigSure was built for Rahul.

 **Coverage Scope:**
GigSure covers **income loss only**. It does not cover:

* Health or medical expenses
* Life insurance
* Accidents or injuries
* Vehicle damage or repair

---

# 👤 Persona

**Name:** Rahul
**Age:** 26
**Profession:** Food Delivery Partner
**Platform:** Zomato / Swiggy
**City:** Hyderabad
**Work Hours:** 8 hours/day
**Daily Earnings:** ₹800 – ₹1,200

Because Rahul is paid per delivery, **any disruption immediately reduces his income.** He operates on a week-to-week financial cycle — GigSure matches this with weekly insurance pricing.

---

# 📖 Scenario Examples

### 🌧️ Scenario 1 — Heavy Rain

Heavy rainfall hits Hyderabad (>70mm/hr) on a Tuesday evening.

Rahul cannot safely ride. He loses 4 hours of the dinner rush — his highest earning window.

GigSure detects the rainfall via Weather API, confirms his zone is affected, and calculates:

```
4 hours lost × ₹119/hr (Rahul's verified hourly rate) × 80% = ₹380 credited to UPI
```

The money arrives before the rain stops. Rahul never opened the app.

---

### 🌡️ Scenario 2 — Extreme Heat

Temperature hits 46°C in Hyderabad. Authorities issue a heat advisory — outdoor work is unsafe between 11 AM and 3 PM.

Rahul loses 3 hours of the lunch rush.

```
3 hours lost × ₹119/hr × 75% = ₹268 credited to UPI
```

GigSure detects the advisory. The zone advisory is proof — Rahul does not need to show he stayed indoors.

---

### 🚫 Scenario 3 — Curfew or Strike

A sudden local strike blocks restaurant pickup zones for 6 hours.

GigSure detects the disruption via civic alerts. The zone closure is the proof — not Rahul's individual inactivity.

```
6 hours lost × ₹119/hr × 85% = ₹605 credited to UPI
```

---

### 😷 Scenario 4 — Severe Air Pollution

AQI crosses 420 (Hazardous) in Rahul's zone. Outdoor work becomes a genuine health risk.

Rahul chose to go out anyway and wore a mask. He still receives the payout — GigSure compensates for the zone condition, not the individual's choice.

```
5 hours affected × ₹119/hr × 70% = ₹416 credited to UPI
```

---

### 📵 Scenario 5 — Platform Downtime

Swiggy's app goes down for 3 hours on a Saturday evening — peak earning time.

Rahul cannot receive any orders through no fault of his own.

```
3 hours lost × ₹119/hr × 65% = ₹232 credited to UPI
```

---

# ⚙️ Application Workflow

```
Worker Registration
 ↓
Earnings Data Pulled from Platform API
 ↓
Hourly Rate Calculated and Confirmed by Worker
 ↓
Zone Mapped + AI Risk Profile Generated
 ↓
Weekly Policy Selected and Purchased
 ↓
Real-Time Event Monitoring (every 30 minutes)
 ↓
Parametric Trigger Detected in Worker's Zone
 ↓
Policy Confirmed Active
 ↓
Payout Calculated: Hours × Rate × Trigger %
 ↓
Fraud Detection Runs (Isolation Forest)
 ↓
Claim Auto-Approved → UPI Payout
 ↓
Worker Notified — Dashboard Updated
```

Workers **never need to manually file a claim.**

---

# 💰 Weekly Premium Model

Gig workers earn and spend week to week. GigSure uses a **7-day pricing cycle** — pay every Monday, covered until Sunday. Cancel anytime.

### 📊 Base Tiers

| Tier | Weekly Premium | Weekly Coverage Cap |
| -------- | -------------- | ------------------- |
| Basic | ₹29 | ₹1,000 |
| Standard | ₹59 | ₹2,500 |
| Pro | ₹99 | ₹5,000 |

---

### 🤖 Dynamic Premium Adjustment

The base tier premium is adjusted by an AI model based on the worker's actual situation.

Factors considered:

| Factor | Adjustment |
|---|---|
| Zone has high historical flood frequency | +₹8/week |
| Zone historically safe from disruptions | −₹5/week |
| No claims in past 12 weeks | −₹3/week |
| High-risk weather forecast for this week | +₹6/week |
| AQI consistently high in zone | +₹4/week |
| Worker operates in high-risk hours (5PM–10PM) | +₹3/week |

```
Final Premium =
Base Tier Price
+ Zone Risk Adjustment
+ Forecast Risk Adjustment
− Safe Zone Discount
```

Every adjustment is shown to the worker transparently before purchase. No hidden factors.

---

### 💸 Payout Calculation

There is no daily cap. Workers receive compensation for what they actually lost.

```
Payout = Hours Lost × Worker's Verified Hourly Rate × Trigger Payout %
```

**How the hourly rate is determined:**

The worker's hourly rate is calculated at onboarding from their platform earnings data (Zomato / Swiggy partner API). It is shown to the worker and confirmed before the policy is purchased. It is locked in for the policy period — the insurer cannot change it after a disruption occurs.

The only ceiling is the **weekly coverage cap**. Within the cap, every rupee of lost income is compensated at the trigger's payout percentage.

> *Premium rates are indicative and will be actuarially validated using historical disruption frequency data in production.*

---

# ⚡ Parametric Triggers

GigSure monitors **10 triggers** across three categories.

### 🌦️ Weather Triggers

| # | Trigger | Condition | Payout % |
|---|---|---|---|
| 1 | Heavy Rainfall | > 50mm in 3 hours | 80% |
| 2 | Severe Flooding | > 100mm in 6 hours | 100% |
| 3 | Extreme Heat | Temperature > 43°C for 4+ hours | 75% |
| 4 | Cyclone / Storm | Wind speed > 60 km/h | 100% |

### 🌫️ Environment Triggers

| # | Trigger | Condition | Payout % |
|---|---|---|---|
| 5 | Unhealthy AQI | AQI 300–400 | 60% |
| 6 | Hazardous AQI | AQI > 400 | 80% |

### 🏙️ Civic & Platform Triggers

| # | Trigger | Condition | Payout % |
|---|---|---|---|
| 7 | Curfew / Section 144 | Active zone curfew | 90% |
| 8 | Transport Strike | Zone blocked > 3 hours | 75% |
| 9 | Zone Sealed | Official zone closure issued | 85% |
| 10 | Platform Downtime | Zomato/Swiggy down > 2 hours | 65% |

Claims trigger only when:

```
External Event Detected in Worker's Zone
AND
Worker's Policy is Active for That Week
```

> **Worker-first design:** Claims are based on zone-level disruption — not individual inactivity. Workers who push through bad conditions are not penalised. The disruption event itself is the proof.

If multiple triggers fire simultaneously, the worker receives the **highest single payout** — not multiple stacked payouts. This keeps the model sustainable.

---

# 📱 Platform Choice

GigSure is built as a **React Web App with Progressive Web App (PWA) support.**

**Why web first:**

* Delivery partners already have multiple apps — a PWA installs without App Store friction
* PWA provides mobile-like experience: installable, push notifications, offline support
* Single codebase serves both the worker mobile interface and the admin desktop dashboard
* React frontend connects to Spring Boot backend via clean REST APIs
* Faster to build and iterate within the 6-week hackathon timeline

**Why not native mobile:**

* Avoids maintaining separate Android and iOS codebases
* PWA covers the mobile use case effectively for our scope
* Admin dashboard is best experienced on desktop — web handles both

---

# 🤖 AI / ML Integration

### 1. 🎯 Risk Profiling at Onboarding

**Model: K-Means Clustering**

Groups workers into risk segments: Low / Medium / High / Very High

Inputs:
* City and delivery zone
* Historical weather disruption frequency (past 2 years)
* Annual AQI trends for the zone
* Time of day the worker typically operates

Output feeds into premium calculation.

---

### 2. 💡 Dynamic Premium Calculation

**Model: XGBoost Regressor**

Takes risk profile + worker income + zone + claim history and outputs an adjusted weekly premium. Output is capped between ₹29 and ₹500 by business rules.

---

### 3. 🔍 Fraud Detection

**Model: Isolation Forest (Anomaly Detection)**

Runs on every claim before payout is released.

Signals monitored:
* GPS coordinates at claim time vs. registered delivery zone
* Time between disruption start and claim filing
* Number of claims filed in past 30 days
* Changes in declared income between policy periods
* Duplicate event ID submissions

Outcome:
* Score < 0.3 → Auto-approved → Instant payout
* Score 0.3–0.7 → Manual review → Resolved within 4 hours
* Score > 0.7 → Blocked → Admin alert fired

> **Worker protection against false flags:** Flagged claims are held for manual review — never silently rejected. Workers are notified immediately with a reason and can appeal within 48 hours. No claim disappears without explanation.

---

### 4. 🔮 Claim Forecasting

**Model: Prophet Time-Series**

Forecasts expected claim volumes for the coming week. Admin sees predicted payout exposure and recommended premium adjustments per zone.

---

# 🧱 Tech Stack

### 🖥️ Frontend
* React 18
* Tailwind CSS
* Recharts
* Axios
* PWA (service workers, installable)

### ⚙️ Backend
* Java — Spring Boot
* Spring Security (JWT authentication)
* Spring Data JPA (ORM)
* MySQL

### 🧠 AI / ML
* Python 3.11
* FastAPI (model serving)
* XGBoost
* scikit-learn (Isolation Forest, K-Means)
* Prophet (forecasting)
* Joblib (model serialization)

### 🌐 APIs
* OpenWeatherMap
* OpenAQ (air quality)
* Razorpay test mode
* Mock Civic Alert API
* Mock Platform Status API

### 🏗️ Infrastructure
* Docker + Docker Compose
* GitHub
* Vercel (React frontend)
* Railway (Spring Boot + ML service)

---

# 📁 Project Structure

```
gigsure/
 README.md
 docker-compose.yml

 frontend/
 src/
 App.jsx
 pages/
 Onboarding.jsx
 Dashboard.jsx
 Policy.jsx
 DisruptionMonitor.jsx
 Claims.jsx
 AdminDashboard.jsx
 components/
 PremiumBreakdown.jsx
 TriggerCard.jsx
 ClaimHistory.jsx
 ZoneHeatmap.jsx

 backend/
 src/main/java/com/gigsure/
 GigSureApplication.java
 config/
 SecurityConfig.java
 JwtConfig.java
 controllers/
 AuthController.java
 WorkerController.java
 PolicyController.java
 ClaimController.java
 TriggerController.java
 AdminController.java
 services/
 PremiumService.java
 TriggerService.java
 ClaimService.java
 PayoutService.java
 FraudService.java
 models/
 Worker.java
 Policy.java
 Claim.java
 Payout.java
 TriggerEvent.java
 integrations/
 WeatherApiClient.java
 AqiApiClient.java
 PaymentGatewayClient.java

 ml/
 risk_model.py
 premium_model.py
 fraud_model.py
 models/
 risk_model.pkl
 premium_model.pkl
 fraud_model.pkl
```

---

# 🗓 Development Plan

### 🟠 Phase 1 — Ideation & Foundation (Mar 4–20)

* [x] Idea validation and market research
* [x] Persona design and scenario mapping
* [x] Premium model and trigger architecture design
* [x] Tech stack selection
* [x] React prototype — all screens working
* [ ] GitHub repository setup with full project structure
* [ ] Record 2-minute strategy video

---

### 🟡 Phase 2 — Automation & Protection (Mar 21–Apr 4)

* [ ] Spring Boot project setup and MySQL schema
* [ ] Worker registration and JWT authentication
* [ ] Policy creation and dynamic premium calculator API
* [ ] OpenWeatherMap and OpenAQ integration
* [ ] All 10 parametric triggers implemented
* [ ] Auto claim processing and payout calculation
* [ ] Razorpay sandbox payout integration
* [ ] React frontend connected to Spring Boot APIs
* [ ] Record 2-minute demo video

---

### 🟢 Phase 3 — Scale & Optimise (Apr 5–17)

* [ ] XGBoost risk and premium ML models
* [ ] Isolation Forest fraud detection model
* [ ] Worker dashboard — live coverage and payout history
* [ ] Admin dashboard — loss ratios, zone heatmap, forecasts
* [ ] Prophet forecasting for admin claim predictions
* [ ] Docker setup for full-stack deployment
* [ ] End-to-end disruption simulation demo
* [ ] Final pitch deck
* [ ] Record 5-minute walkthrough demo video

---

# 👥 Team

| Member | Role |
| -------- | ------------------------- |
| Arjun Mehta | Team Lead — Full Stack (React + Spring Boot) |
| Priya Sharma | Backend — APIs & Database |
| Kiran Reddy | AI / ML — Risk, Premium & Fraud Models |
| Sneha Iyer | UI / UX — Design & Frontend |

Institution: KL University, Hyderabad
Hackathon: Guidewire DEVTrails 2026

---

 Built for **Guidewire DEVTrails 2026** — *Seed. Scale. Soar.*
