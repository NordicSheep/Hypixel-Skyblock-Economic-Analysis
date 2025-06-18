# 📊 Hypixel Bazaar Flipping Performance Tracker

A modular, data-accurate dashboard to track and analyze Bazaar and Auction flipping in Hypixel SkyBlock.

---

## 🎯 Project Goals

- Track profits and ROI using FIFO cost basis
- Analyze trends across item types, tiers, and market tags
- Visualize open positions, breakeven points, and mayor-based opportunities
- Enable configurable fee assumptions for Bazaar and Auction
- Support dynamic dashboard layout and refresh controls
- Prepare for long-term ML-based price trend prediction

---

## 🧩 Core Features

### ✅ Trade Logging
- Manual buy/sell trade entry
- FIFO profit matching
- Minimum Bazaar fee (1.25%) applied on sell offers
- Configurable fee logic

### ✅ Bazaar Snapshot Logger
- Logs market prices once per day at **7 PM**
- Fields: buy/sell prices, volume, timestamp
- Archived monthly (older than 6 months) into `bazaar_snapshots_archive`

### ✅ Profit Calculation Engine
- FIFO trade matching
- Realized profit, cost basis, and TWR tracking
- Break-even logic for open positions

### ✅ Analytics & Performance Metrics

#### Core Reports
- **Realized Profit**
- **Time-Weighted Return (TWR)**  
  _Assumes lowest Bazaar fee — configurable override supported_

- **Grouped Performance Report**  
  Aggregate ROI by:
  - Category (e.g., Farming, Mining)
  - Tier (Common, Epic, etc.)
  - Economy Tag (Dungeon, Essence, etc.)

- **Open Positions Report**
  - Quantity, cost basis, live bid/ask
  - Required break-even unit price
  - Visual gap indicator between cost, breakeven, and current

- **Price Manipulation Flag**
  - Detects items with abnormally high bid-ask spreads
  - Useful for flagging potential market manipulation

---

## 🔥 Mayor Heatmap Module
- Tracks item price behavior before/after mayor elections
- Identifies "mayor-sensitive" items based on historical performance
- Visualized as sortable table/heatmap

---

## 🎯 Auction IRR Module (Separate)
- Calculates Internal Rate of Return on auction flips
- Assumes:
  - 1% sale fee
  - 2% listing fee  
  _Configurable for future fee changes_

- Tracks:
  - Time held
  - Coins in/out
  - Final IRR per flip

---

## 🖥️ Frontend (React + Tailwind CSS)
- Built with **React + Tailwind**
- Layout grid: powered by `react-grid-layout`
- Features:
  - Drag & resize modules
  - Save layout preferences
  - Toggle auto-refresh (5 min intervals)
  - Manually enable/disable data updates

---

## 🌱 Optimistic Features (Stretch Goals)

### I. Volatility Classification  
Flag items with unstable spread/price patterns

### II. Liquidity Scoring  
Rank items by average turnover speed

### III. Historical Profit Consistency  
Score items by % of profitable weeks or time intervals

### IV. Mayor Sensitivity Index  
Assign sensitivity scores based on item response to specific mayors

### V. Time-in-Trade Analysis  
Track and visualize average hold durations by item or tag

---

## 🔮 Long-Term Stretch Goal: ML-Based Price Prediction

Implement machine learning models to:
- Predict item-specific Bazaar price trends
- Forecast ROI for different items using:
  - Historical snapshots
  - Grouped performance patterns
  - Mayor trends

### Includes Mayoral Sequence Modeling:
- Analyze how **specific sequences of mayors** affect item prices
- For example: Aatrox → Paul may cause different results than Aatrox → Diana
- Uses sequential/temporal models like LSTM or Prophet

---

## 🧰 Tech Stack

| Layer       | Stack                          |
|-------------|--------------------------------|
| Frontend    | React + Tailwind CSS           |
| Charts      | Recharts / Chart.js            |
| Backend     | Python (FastAPI or Flask)      |
| Database    | MySQL                          |
| Scheduler   | Cron / Async Tasks (daily @ 7) |
| Data Source | Hypixel API + Manual Entry     |

---

## 📂 Suggested Repo Structure

```
/client            → React + Tailwind frontend
/server            → Python backend API
/database          → MySQL schemas, archive scripts
/snapshots         → Daily logging logic
/utils             → Fee utilities, spread detection
/docs              → README, roadmap, reference
```

---

## 🛠️ Development Roadmap

### Phase 1: Backend Infrastructure
- [ ] MySQL schemas
- [ ] FIFO profit logic
- [ ] Manual trade entry API

### Phase 2: Snapshot Logging & Archiving
- [ ] Daily logging at 7 PM
- [ ] Archive snapshots monthly
- [ ] Build live price fetch endpoint

### Phase 3: Core Analytics
- [ ] Grouped performance report
- [ ] Open positions w/ break-even gap visual
- [ ] Flag price manipulation

### Phase 4: Frontend Dashboard
- [ ] Modular UI w/ toggleable modules
- [ ] Auto-refresh toggle
- [ ] React-grid layout

### Phase 5: Bonus Features
- [ ] Auction IRR
- [ ] Optimistic insight layers
- [ ] Machine learning (long term)

---

## License

MIT License. Not affiliated with Hypixel or Mojang.
