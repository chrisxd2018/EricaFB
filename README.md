# EricaFB — Personal Finance Dashboard

A self-contained personal finance dashboard built with plain HTML, CSS, and JavaScript. No build step, no dependencies to install. Tracks income, expenses, investment property, savings goals, and scenario planning — with all values editable live in the browser.

**Live site:** https://chrisxd2018.github.io/EricaFB/

---

## Features

- **Dashboard** — Monthly income, expenses, net cash flow, savings balance, quick insights
- **Income** — Salary and rental income (fortnightly → monthly normalised)
- **Expenses** — Full categorised breakdown: mortgage, OC fee, bills, utilities, transport, insurance, AASW, food, lifestyle, travel, savings
- **Property** — Single investment property: rental income vs mortgage + OC fee, net cash flow, cover ratio
- **Savings Goals** — Progress bars with ETA for house deposit, emergency fund, long-term wealth
- **Scenario Planner** — Toggle Base/Scenario mode; edit any field without overwriting base; Apply or Discard
- **Comparison** — Side-by-side line table + bar chart of base vs scenario values
- **Executive Summary** — Dynamic risks, opportunities, priorities generated from live figures
- **Local Storage** — All changes persist across browser sessions
- **Reset** — One-click restore to spreadsheet defaults
- **Mobile responsive** — Sidebar collapses to hamburger menu

---

## Pay Cycle Note

Erica's spreadsheet uses a **fortnightly** pay cycle (×26/year). All values in the app are stored and displayed as **monthly equivalents** (fortnightly × 26 ÷ 12). Fortnightly figures are shown as a reference below each input.

---

## Local Development

Open `index.html` directly in any modern browser — no server or build step needed:

```bash
# Windows
start index.html

# macOS / Linux
open index.html
```

Chart.js is loaded from CDN — an internet connection is required for charts.

---

## Deploy to GitHub Pages

### 1. Clone and push

```bash
git clone https://github.com/chrisxd2018/EricaFB.git
cd EricaFB
git add .
git commit -m "Initial EricaFB dashboard"
git push origin main
```

### 2. Enable GitHub Pages

1. Go to **Settings → Pages** in the GitHub repo
2. Under **Source** → select **Deploy from a branch**
3. Branch: `gh-pages` / Folder: `/ (root)` → **Save**

GitHub Actions deploys automatically on every push to `main`. No manual secrets needed — uses the built-in `GITHUB_TOKEN`.

### Expected URL

```
https://chrisxd2018.github.io/EricaFB/
```

---

## Updating Data

All financial data is hardcoded inline in `index.html` inside the `const DEFAULTS = { ... }` object. Search for `DEFAULTS` to find the values and update them.

| What to change | Where |
|---|---|
| Salary, rental income | `salary`, `rentIncome` in `DEFAULTS` |
| Mortgage, OC fee | `mortgage`, `oc` in `DEFAULTS` |
| Bills, utilities | `electricity`, `water`, `hotWater`, `internet`, `netflix` |
| Transport, insurance | `transport`, `healthIns`, `carIns` |
| Lifestyle | `dating`, `gym`, `celebrations`, `travel` |
| Savings contribution | `savingsMo` |
| Current savings balance | `savBal` |
| Goal targets | `goalDeposit`, `goalEmergency`, `goalWealth` |

---

## Spreadsheet Differences vs ChrisFB

| Feature | ChrisFB | EricaFB |
|---|---|---|
| Pay cycle | Monthly (×12) | Fortnightly (×26) |
| Income sources | Salary + bonus + 2× rental | Salary + 1× rental |
| Properties | 2 investment + own rent | 1 investment property |
| Unique expenses | Malaysia, lunch, dinner | AASW membership, Netflix, travel, celebrations |
| Savings starting balance | $25,000 | $82,160 |
| Savings rate | $1,400/mo (12.1%) | $2,693/mo (34.9%) |
| Primary savings goal | Personal safety net $60k | House deposit $140k |

---

## Tech Stack

| Layer | Technology |
|---|---|
| Markup | HTML5 |
| Styling | CSS3 (no framework) |
| Charts | [Chart.js 4.4](https://www.chartjs.org/) via CDN |
| Logic | Vanilla JavaScript (ES6) |
| Hosting | GitHub Pages |
| CI/CD | GitHub Actions + peaceiris/actions-gh-pages |

---

## Assumptions

- All values are in AUD
- Fortnightly values converted to monthly as: `value × 26 ÷ 12`
- Savings balance of $82,160 taken from 12 Apr 2026 row in the saving sheet
- House deposit goal of $140,000 inferred from the escalating Goal column in the saving sheet (reaches ~$140k by Mar 2027)
- Emergency fund goal of $50,000 is a reasonable inferred target (not explicitly stated in spreadsheet)
- AASW = Australian Association of Social Workers professional membership fee
- OC = Owner Corporation (strata) fee on investment property
- No explicit bonus income found in Erica's spreadsheet; an optional bonus field can be added if needed
