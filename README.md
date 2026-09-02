# M&A Deal Structuring & Capital Markets Engine

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![Framework](https://img.shields.io/badge/Streamlit-1.35%2B-FF4B4B.svg)](https://streamlit.io/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

An institutional-grade **M&A Accretion / Dilution Engine** and **Capital Structure Optimizer** built in Python. This platform models complex corporate transactions, Purchase Price Allocations (PPA), debt/equity financing considerations, synergy tax shields, and interactive 2D sensitivity matrices for investment banking and corporate development workflows.

---

## 🎯 Executive Overview & Core Features

* **Dynamic Accretion / Dilution Analysis:** Computes pro-forma combined Net Income, standalone vs. pro-forma EPS, and overall deal accretion/dilution percentages.
* **Financing Mix & Consideration Modeling:** Real-time optimization between Cash/Debt financing and Stock issuance with customizable borrowing costs.
* **Synergies & Interest Expense Adjustments:** Models pre-tax operating synergies, corporate tax shields, and interest costs on newly issued acquisition debt.
* **2D Sensitivity Matrix Grid:** Interactive stress testing evaluating **Offer Premium (%)** against **% Cash Financed** to determine accretive boundaries.
* **Executive Deal Summary Dashboard:** Visual bridge for EPS comparison, capital allocation pie charts, and key valuation metrics ($EV/EBITDA$, implied $P/E$).

---

## 📐 Mathematical Architecture & Financial Logic

### 1. Offer & Purchase Price Allocation
$$\text{Offer Price per Share} = \text{Target Share Price} \times \left(1 + \text{Premium \%}\right)$$

$$\text{Equity Purchase Price} = \text{Offer Price per Share} \times \text{Target Shares Outstanding}$$

$$\text{Enterprise Purchase Price} = \text{Equity Purchase Price} + \text{Target Net Debt}$$

### 2. Consideration & Pro-Forma Share Count
$$\text{Cash Consideration} = \text{Equity Purchase Price} \times \text{\% Cash Financed}$$

$$\text{Stock Consideration} = \text{Equity Purchase Price} \times \left(1 - \text{\% Cash Financed}\right)$$

$$\text{New Shares Issued} = \frac{\text{Stock Consideration}}{\text{Acquirer Share Price}}$$

$$\text{Pro-Forma Shares} = \text{Acquirer Shares Outstanding} + \text{New Shares Issued}$$

### 3. Pro-Forma Income Statement Adjustments
$$\text{Pro-Forma Net Income} = \text{Acquirer NI} + \text{Target NI} + \text{Synergies} \times (1 - \tau) - \text{Interest Expense} \times (1 - \tau)$$

$$\text{Pro-Forma EPS} = \frac{\text{Pro-Forma Net Income}}{\text{Pro-Forma Shares}}$$

$$\text{\% Accretion / Dilution} = \left( \frac{\text{Pro-Forma EPS} - \text{Acquirer Standalone EPS}}{\text{Acquirer Standalone EPS}} \right) \times 100$$

---

## 🛠️ Tech Stack & Directory Structure

* **Core Logic:** Python (`Pandas`, `NumPy`)
* **Analytics & Modeling:** `SciPy`, `Math`
* **Interactive Dashboard:** `Streamlit`
* **Data Visualization:** `Plotly`

```text
ma-deal-structuring-engine/
├── data/                      # Sample financial datasets & deal cases
├── src/
│   ├── __init__.py
│   ├── ma_engine.py           # Core accretion/dilution & sensitivity math
│   └── visualizer.py          # Plotly chart generation utilities
├── .gitignore
├── README.md                  # Institutional documentation
├── app.py                     # Streamlit multi-tab Web Application
└── requirements.txt           # Python dependencies
