# My Finance Buddy — V1 (MVP) Feature Specification

**Version:** 1.0  
**Prepared for:** Design & Engineering Teams  
**Scope:** MVP for international master’s students in the U.S.  
**Focus:** Monthly cashflow clarity, motivation, and simplicity  

---

## Table of Contents

1. Product Overview
   - Problem Statement
   - Motivation / North Star
   - Goals of the MVP
2. V1 Feature Set (MVP Scope)
   - Expense Input (Manual-First)
   - Monthly Dashboard (Primary Home Screen)
   - Monthly Budget Setup
   - Currency Conversion (Core Differentiator)
   - Recurring Expense Reminders
   - Insights & Motivational Nudges
   - Categories + Tags
   - Onboarding Experience
3. User Journeys
4. Design System Requirements
5. Technical Requirements
   - Tech Stack
   - Data Model (Simplified)
6. What’s Not in V1
7. Success Metrics
8. MVP Delivery Plan

---

## 1. Product Overview

### 1.1 Problem Statement

International master’s students in the U.S. struggle to manage money because of:

- Limited or inconsistent income (part-time work or parental support)
- High monthly expenses (rent, groceries, utilities, school costs)
- Unfamiliarity with the U.S. financial system (subscriptions, hidden fees, credit, taxes)
- Fragmented tools (Excel sheets, bank apps, Venmo/Zelle, notes)
- Constant need to convert USD into home currency to understand value

Result: overspending, stress, and difficulty staying on top of monthly finances.

### 1.2 Motivation

My Finance Buddy helps international students stay on top of monthly spending in a simple, motivating way—so they can save smart, avoid overspending, and still enjoy life in the U.S.

### 1.3 Goals of the MVP

- Deliver monthly cashflow clarity
- Make expense tracking fast, simple, and contextually meaningful
- Reduce financial stress by showing USD + home currency in one place
- Keep students motivated and consistent through lightweight rewards
- Build foundation for long-term budgeting features

---

## 2. V1 Feature Set (MVP Scope)

### 2.1 Expense Input (Manual-First)

**Purpose:** Enable fast, painless recording of daily spending (cash, Venmo, Zelle, mixed sources).

**Requirements:**
- Prominent “Add Expense” button available on all major screens
- Input fields:
  - Amount
  - Currency selector (USD or Home Currency)
  - Category (Food, Groceries, Rent, Transport, Utilities, School, Shopping, Misc)
  - Optional note (e.g., “Bubble tea”, “Uber to campus”)
- Auto-conversion between currencies using daily exchange rate (pulled once per day)
- 5-second flow: select → type → save

**Acceptance Criteria:**
- Expense can be added in ≤ 5 taps
- Home currency conversion visible immediately
- Expense saved to the current month by default

### 2.2 Monthly Dashboard (Primary Home Screen)

**Purpose:** Give users a clear, motivating snapshot of their month at a glance.

**Must include:**
- Total spent this month
- Remaining monthly budget
- Visual progress bar for spending
- Category-level breakdown (simple bar or donut chart)
- Home currency equivalent at the top (e.g., “This month: $842 ≈ ₹70,125”)

**Contextual nudges:**
- “At this pace, you may overspend by $62.”
- “You’re doing good. You’re below your expected pace.”

**Interactions:**
- Tap a category → open list of expenses
- Tap month → switch to previous months (read-only)

### 2.3 Monthly Budget Setup

**Purpose:** Help students define a realistic limit and avoid month-end surprises.

**Features:**
- Set monthly spending limit during onboarding
- Optional category budgets
- Visual “Budget Remaining” indicator updated real-time
- Alerts when nearing thresholds (75% spent, projected overspend)

**Acceptance Criteria:**
- User can set/edit budgets anytime
- Budget updates reflect instantly on the dashboard

### 2.4 Currency Conversion (Core Differentiator)

**Purpose:** Help students mentally connect U.S. spending with home currency value.

**Features:**
- Store user’s home currency selected during onboarding
- Automatic conversion for every recorded expense
- Summary shown in both USD and home currency
- Exchange rate updated once per day via API
- Display friendly equivalents (e.g., “This coffee = ₹412”) 

**Acceptance Criteria:**
- No error in conversion logic
- Currency visible in dashboard + input screens
- Exchange rate clearly shown (e.g., “Rate: 1 USD = ₹83.3”)

### 2.5 Recurring Expense Reminders

**Purpose:** Ensure students never miss predictable monthly payments.

**Features:**
- User sets recurring items (Rent, Phone Plan, Internet, Subscriptions)
- Choose recurring cycle: monthly
- Reminder notification 1 day before
- Reminders displayed on dashboard as upcoming items

**Acceptance Criteria:**
- Reliable notification delivery
- Items listed under “This Month’s Essentials”

### 2.6 Insights & Motivational Nudges

**Purpose:** Make budgeting encouraging, not stressful.

**Features:**
- Micro-achievements (e.g., “You tracked 7 days in a row!”)
- Positive messages when spending improves (e.g., “Grocery spending 20% below usual”)
- Weekly summaries (USD + home currency)
- Targeted alerts (e.g., “Dining-out spending increased 40% from last week.”)

**Tone:** Friendly, encouraging, never judgmental.

### 2.7 Categories + Tags

**Purpose:** Improve insights and organization.

**Features:**
- Predefined categories
- Optional custom tags
- Category colors consistent across dashboard
- Tap category → list of expenses

### 2.8 Onboarding Experience

**Purpose:** Create clarity from the start.

**Flow:**
1. Welcome → Motivation statement
2. Select home currency
3. Set monthly budget
4. Add an example expense (guided step)
5. Completion → “You’re ready to track your month!”

**Acceptance Criteria:**
- Completed in < 2 minutes
- Home currency & budget stored immediately

---

## 3. User Journeys

### Journey A: First-Time User Onboarding

- Trigger: Student downloads app after struggling with budgeting.
- Steps: Open app → friendly welcome → choose home currency → set monthly budget → tutorial adds a sample expense → lands on Monthly Dashboard
- Outcome: User understands purpose and sees value instantly.

### Journey B: Daily Tracking Behavior

- Trigger: User buys food for $9.50.
- Steps: Open app → tap “Add Expense” → enter amount → choose category Food → save → dashboard updates → micro-nudge “Nice! You tracked your expenses today ⚡️”
- Outcome: Habit formation and positive reinforcement.

### Journey C: Nearing Overspend

- Trigger: 75% of budget spent with 10 days left.
- Steps: Dashboard warning → prediction “At this pace, you may overspend by $40” → tap for category breakdown → identify overspending category → adjust behavior
- Outcome: Supports smarter decisions without guilt.

### Journey D: Monthly Reflection

- Trigger: Month ends.
- Steps: User sees summary (Total spent USD + home currency, category breakdown, improvement areas) → seasonal nudge “You did great staying on track!” → new month resets automatically
- Outcome: Reinforces progress and motivation.

---

## 4. Design System Requirements (High-Level)

- Clean, friendly interface
- Soft colors, minimal gradients
- Culturally inclusive illustrations
- Emphasis on clarity: large numbers, simple charts
- Motivational microcopy with friendly tone
- Accessible color contrast
- Warm, not corporate, onboarding

---

## 5. Technical Requirements (Engineering)

### 5.1 Tech Stack (Recommended)

- Frontend: React + TypeScript
- UI styling: Tailwind CSS (good for quick responsive layouts)
- Database: Browser storage, using:
    - localStorage for simplest implementation, or
    - localforage (wraps IndexedDB, more robust)
- Currency API: Fixer.io, ExchangeRate-API, or a suitable free alternative

### 5.2 Data Model (Optimized for Browser Storage)

**Core Entities:**

- **User** (single instance per browser)
  - id (UUID)
  - homeCurrency (string, e.g., "INR", "GBP")
  - monthlyBudget (number, in USD)
  - onboardingCompleted (boolean)
  - createdAt (timestamp)
  - updatedAt (timestamp)

- **Expense**
  - id (UUID)
  - amountUSD (number)
  - amountHomeCurrency (number, cached at time of entry)
  - exchangeRateUsed (number, e.g., 83.3, the rate applied to this expense)
  - exchangeRateDate (string, format "YYYY-MM-DD", which day's rate was used)
  - category (string: "Food", "Groceries", "Rent", "Transport", "Utilities", "School", "Shopping", "Misc")
  - tags (string array, optional custom tags)
  - note (string, optional)
  - timestamp (when the expense occurred)
  - month (string, format "YYYY-MM" for fast querying)
  - createdAt (when logged in app)
  - updatedAt (timestamp)
  - deleted (boolean, for soft deletes)

- **BudgetLimit** (for category-level budgets)
  - id (UUID)
  - category (string: "Food", "Rent", etc., or "TOTAL" for monthly overall budget)
  - limitUSD (number)
  - month (string, format "YYYY-MM", allows different budgets per month)
  - createdAt (timestamp)
  - updatedAt (timestamp)

- **RecurringExpense**
  - id (UUID)
  - name (string, e.g., "Rent", "Netflix", "Phone Plan")
  - amountUSD (number)
  - dueDay (number, 1-31, day of month expense is due)
  - frequency (string, "monthly" for V1)
  - category (string, for dashboard grouping)
  - active (boolean)
  - notifiedMonths (string array, tracks which months user was reminded, e.g., ["2025-11", "2025-12"])
  - createdAt (timestamp)
  - updatedAt (timestamp)

- **Achievement** (for micro-achievements)
  - id (UUID)
  - type (string: "7-day-streak", "under-budget", "first-expense", "consistent-tracker")
  - earnedAt (timestamp)
  - month (string, format "YYYY-MM", for monthly reset of streaks)
  - description (string, friendly message shown to user)

- **ExchangeRate** (cached daily)
  - id (UUID)
  - currency (string, e.g., "INR")
  - rateToUSD (number)
  - date (string, format "YYYY-MM-DD", one rate per currency per day)
  - lastUpdated (timestamp)

**Data Model Rationale:**
- No user_id FK on entities (single-user app, simplifies queries)
- `month` field on Expense enables fast filtering by month without date parsing
- `notifiedMonths` on RecurringExpense prevents duplicate reminder notifications
- `deleted` flag on Expense allows data integrity without losing records
- `BudgetLimit` supports both overall monthly budget and optional category budgets
- `Achievement` model enables micro-motivations per month
- `exchangeRateUsed` and `exchangeRateDate` on Expense preserve conversion audit trail

### 5.3 Currency Conversion Flow

**Overview:** Currency conversion happens at the moment an expense is logged. The exchange rate is cached with the expense to maintain historical accuracy and enable fast queries.

**Conversion Process:**

1. **User Adds Expense**
   - User enters amount (in USD or home currency)
   - App retrieves today's exchange rate from `ExchangeRate` table for user's `homeCurrency`
   - If rate not available locally, fetch from API and cache in `ExchangeRate` table (once per day)

2. **Conversion Logic**
   - If user enters in USD: `amountHomeCurrency = amountUSD × rateToUSD`
   - If user enters in home currency: `amountUSD = amountHomeCurrency ÷ rateToUSD`
   - Round home currency to 2 decimal places for display

3. **Storage**
   - Store `amountUSD` (canonical, always in USD)
   - Store `amountHomeCurrency` (cached converted value)
   - Store `exchangeRateUsed` (the specific rate applied, e.g., 83.3)
   - Store `exchangeRateDate` (which day's rate was used, "YYYY-MM-DD")

4. **Display to User**
   - Show both amounts: "$9.50 ≈ ₹790" (using cached values)
   - Show rate transparency: "Rate: 1 USD = ₹83.3 (Nov 29)"

5. **Dashboard Calculations**
   - All monthly totals use cached `amountUSD` (never recalculate)
   - Home currency total = sum of all `amountHomeCurrency` for the month
   - No need to join with `ExchangeRate` table for dashboard queries (fast)

**Benefits:**
- ✅ Historical accuracy: each expense locked to the rate at the time it was logged
- ✅ Transparency: users see exactly which rate was applied
- ✅ Performance: dashboard queries are O(1), no conversion needed on reads
- ✅ Audit trail: can see why historical conversions differ if rates changed

**Example:**
```
Nov 29: User logs $10 expense when rate is 1 USD = ₹83
  → Stored as: amountUSD=10, amountHomeCurrency=830, exchangeRateUsed=83, exchangeRateDate=2025-11-29

Dec 1: Rate changes to 1 USD = ₹82 (but Nov expense stays locked)
  → Historical expense still shows ₹830 (not ₹820)
  → User can see "Rate was ₹83 on Nov 29"
```

---

## 6. What’s Not in V1 (Intentional Exclusions)

- Roommate splitting
- Bank integrations (Plaid)
- Subscription cancellation tools
- Credit score features
- Tax estimations
- Long-term savings plans
- Automated AI insights
- Income tracking
- Tuition planning
- Investment suggestions

Reason: Maintain focus on monthly cashflow clarity and a small, high-value surface area for fast delivery.

---

## 7. Success Metrics (MVP Validation)

- Daily tracking habit: % users adding ≥1 expense/day
- Weekly active users (WAU)
- Reduction in overspending warnings month-over-month
- 30-day retention
- Number of expenses logged/user/month
- Onboarding completion rate
- Frequency of currency switching usage

---

## 8. MVP Delivery Plan (Recommended)

- Phase 1: Foundation (2–3 weeks)
  - Onboarding, Expense input, Currency conversion, Basic database models

- Phase 2: Dashboard + Budget (3–4 weeks)
  - Monthly dashboard, Budget logic, Category visuals

- Phase 3: Alerts + Motivation (2 weeks)
  - Recurring reminders, Overspending warnings, Micro-achievements

- Phase 4: Polish & QA (1–2 weeks)
  - Visual refinement, Usability testing, Performance checks, Store prep

---

If you want, I can also produce: a clickable Figma structure/wireframe plan, detailed user flows, a project timeline (Gantt), or a pitch deck. Tell me which one you want next.