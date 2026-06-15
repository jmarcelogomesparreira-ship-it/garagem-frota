# 🚗 Garagem 3D — Fleet Management Visual

An interactive 3D fleet management visualization built for embedding in Power BI via HTML Content visual.

![Three.js](https://img.shields.io/badge/Three.js-r128-black?style=flat-square&logo=three.js)
![Power BI](https://img.shields.io/badge/Power%20BI-Compatible-yellow?style=flat-square&logo=powerbi)
![License](https://img.shields.io/badge/License-MIT-blue?style=flat-square)

---

## ✨ Features

- **3D parking lot** with up to 200+ vehicles rendered in real time using Three.js r128
- **Dynamic grouping** by area, sub-area, unit and rental company — add or remove groups directly in the data layer, no code changes needed
- **Color-coded vehicle status:**
  - 🟢 OK — no pending items
  - 🟡 Attention — items due soon
  - 🔴 Pending — overdue items requiring action
  - 🔵 Available — unallocated vehicle
  - 🟣 Replacement due — scheduled swap within 30 days
  - 🟠 KM Warning — over 90% of contracted kilometers used
- **KM contract tracking** per vehicle — consumed vs contracted, saldo and visual progress bar
- **Scheduled replacement alerts** with a dedicated panel listing vehicles due within 60 days
- **Blinking headlights** on vehicles with critical alerts
- **Full camera control** — orbit (left drag), pan (right drag / Ctrl+drag) and zoom (scroll)
- **Sidebar panels:** KPI overview, filters, replacement schedule and full vehicle detail on click
- **Configurable alert types** — add new checklist items without touching the rendering logic

---

## 🛠 Tech Stack

| Layer | Technology |
|---|---|
| 3D Rendering | Three.js r128 (CDN) |
| Language | ES5 JavaScript (Power BI compatible) |
| Architecture | Single HTML file |
| Data Layer | JSON object (replaceable with Power BI parameters) |
| Hosting | GitHub Pages |

---

## 📁 Project Structure

```
garagem-frota/
│
├── index.html      # Main file — full visual, logic and data in one file
└── README.md
```

---

## ⚙️ Data Configuration

All data is defined at the top of `index.html` in clearly marked sections:

```javascript
// Alert/checklist types — add as many as needed
var TIPOS_PENDENCIA = ['Inspection', 'Checklist', 'Tracker', 'Maintenance', 'Wash', 'Fuel'];

// Rental companies
var LOCADORAS = ['Company A', 'Company B', 'Company C', 'Company D'];

// Units / fleet groups
var UNIDADES = ['Unit 1', 'Unit 2', 'Unit 3', 'Unit 4'];

// Areas and sub-areas — fully dynamic
var ESTRUTURA = {
  'Agriculture':    ['Management', 'Coordination', 'Cultivation', 'Harvest'],
  'Industrial':     ['Management', 'Processing', 'Maintenance'],
  'Administrative': ['HR', 'Finance', 'IT'],
  'Maintenance':    ['Mechanics', 'Fleet', 'Warehouse']
};
```

Replace the `gerarFrota()` function with your real dataset or connect via Power BI parameters.

---

## 📊 Power BI Integration

### 1. Host on GitHub Pages

1. Upload `index.html` to this repository
2. Go to **Settings → Pages**
3. Set source to **main branch / root**
4. Your visual will be available at:
   `https://your-username.github.io/garagem-frota/`

### 2. Embed in Power BI

1. Install the **HTML Content** visual (AppSource)
2. Create a DAX measure:

```dax
Fleet Visual URL = "https://your-username.github.io/garagem-frota/"
```

3. Add the HTML Content visual to your report page
4. Drag the measure into the **HTML** field
5. Resize the visual to fill the page

---

## 🚀 Roadmap

- [ ] Power BI parameter integration for real-time data binding
- [ ] Page 2: KPI bar charts by rental company and area
- [ ] Page 3: KM consumption heatmap and replacement timeline
- [ ] CSV/Excel import support

---

## 📄 License

MIT — free to use, adapt and distribute.
