# Interactive AntiScam Dashboard: HTML Prototype Prompt

## PROJECT BRIEF FOR DEVELOPER/DESIGNER

**Goal:** Create a single-page, fully interactive HTML5 dashboard that visualizes financial fraud data from Russian research (ЦБ РФ).

**What you're building:** A professional, production-ready dashboard with no backend needed (all data hardcoded for MVP). This will be shown to decision-makers, banks, and regulators.

---

## DESIGN SYSTEM & COLORS

Use this professional color palette:
- **Primary (Trust):** #2578CB (Blue) — for main CTAs, highlights
- **Success:** #22C55E (Green) — recovery, protection
- **Warning/Risk:** #EF4444 (Red) — fraud, danger
- **Secondary:** #F59E0B (Orange) — elderly victims, medium risk
- **Dark BG:** #0F172A (Slate-900) — main background
- **Card BG:** #1E293B (Slate-800) — dashboard cards
- **Text:** #E2E8F0 (Slate-200) — light text on dark
- **Text Secondary:** #94A3B8 (Slate-400) — secondary text
- **Accent Purple:** #A855F7 (Purple) — credit trap, financial stress

Font: `Inter, -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif`

---

## STRUCTURE: 4 MAIN SECTIONS

### SECTION 1: HEADER + QUICK STATS

**Visual:** Modern header with logo, title, and 6 KPI cards in a row

```
┌─────────────────────────────────────────────────────────┐
│  AntiScam Dashboard | ЦБ РФ Financial Fraud Analysis   │
└─────────────────────────────────────────────────────────┘

┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐ ...
│ Жертвы   │ │ Убытки   │ │ Контакт  │ │ Восст.   │
│ 7.1M     │ │ 98.4B₽   │ │ 36.7%    │ │ 14.6B₽   │
│ +37%↑    │ │ +35%↑    │ │ +23%↑    │ │ +3%↑     │
└──────────┘ └──────────┘ └──────────┘ └──────────┘
```

**KPIs to display (2025 data):**
- Жертвы мошенничества: 7.1M (с динамикой +37% vs 2024)
- Убытки: 98.4B₽ (+35% vs 2024)
- % контакта с мошенничеством: 36.7% (+23% vs 2024)
- Восстановление: 14.6B₽ (+3% vs 2024)
- Скорость обнаружения: 48 часов
- 2FA внедрение: 35%

---

### SECTION 2: FRAUD CHANNELS (SANKEY DIAGRAM + TABLE)

**Left Part: Interactive Sankey Diagram**
```
Input (Channels)  →  Penetration  →  Conversion to Loss
─────────────────────────────────────────────────────────
 Телефон 54.6%    →    83.1%     →    27.5%    (42.7k₽)
 Мессенджер 16.1% →    28.7%     →    35.2%    (55-120k₽)
 Соцсети 12.1%    →    18.8%     →    22.1%    (25-75k₽)
 Поддельный сайт  →    5.9%      →    41.3%    (50-200k₽)
 Госуслуги 3.8%   →    12.7%     →    18.4%    (15-60k₽)
 Вирусы 3.3%      →    3.2%      →    52.1%    (100-500k₽)
```

**Implementation:**
- Use interactive flow/Sankey visualization (can use Chart.js, Recharts, or D3.js)
- Hover over each flow → tooltip shows exact numbers
- Flow thickness = attempt volume
- Color gradient: green (SMS, low harm) → red (Viruses, extreme harm)
- Click channel → expands to show attack tactics below

**Right Part: Channel Performance Table**

| Канал | Попытки | Проникновение | Конверсия | Средний убыток | Тренд |
|-------|---------|---------------|-----------|----------------|-------|
| Телефон/СМС | 54.6% | 83.1% ⚠️ | 27.5% | 42.7k₽ | ↑ +18% |
| Мессенджер | 16.1% | 28.7% | 35.2% ⚠️ | 55-120k₽ | ↑ +22% |
| Соцсети | 12.1% | 18.8% | 22.1% | 25-75k₽ | → Stable |
| Поддельный сайт | 4.8% | 5.9% | 41.3% ⚠️ | 50-200k₽ | ↓ -5% |
| Госуслуги | 3.8% | 12.7% | 18.4% | 15-60k₽ | ↑ +15% |
| Вирусы | 3.3% | 3.2% | 52.1% 🔴 | 100-500k₽ | ↓ -8% |

---

### SECTION 3: VICTIM PROFILES (5 TABS)

**Tab Navigation at top:**
```
[Напряженный профессионал] [Пожилой] [Молодежь] [Кредитная ловушка] [Случайная жертва]
         35%                   25%       18%           12%               10%
```

**Each tab shows:**

#### TAB 1: Stressed Professional (35%)
- **Demographics:** 25-44 лет | Доход 150-400k₽/мес | Город 75%
- **Financial Impact:** 
  - Средний убыток: 85k₽
  - Восстановление: 8%
  - Кумулятивный ущерб: 187.4B₽
- **Risk Factors:** Спешка | Доверие авторитету | Слабая проверка ссылок
- **Attack Vectors:** SMS спуфинг (54.6%), социнженерия, срочность
- **Protection:** Real-time push (>50k₽), биометрия, 24ч восстановление
- **ROI:** 5.2x

**Visual for each profile:**
- Left: Risk gauge (0-100 scale, color-coded) showing their risk level
- Center: Behavioral indicators as horizontal bars
- Right: Protection timeline and cost-benefit analysis
- Bottom: Success story (anonymized case study)

#### TAB 2: Isolated Elderly (25%)
- **Demographics:** 55-80 лет | Доход 30-100k₽/мес | Провинции 65% | Одиночество 72%
- **Financial Impact:**
  - Средний убыток: 45k₽
  - Восстановление: 22%
  - Кумулятивный ущерб: 95.4B₽
  - Психологический ущерб: 48% прекращают банкинг
- **Risk Factors:** Низкая цифровая грамотность | Доверие голосу | Эмоциональная уязвимость
- **Attack Vectors:** "Внук в беде" (45%), звонок из банка, TeamViewer, эмоциональное давление
- **Protection:** Простой UI, горячая линия 1-800-MOSHENNSTVO, ТВ/радио образование, "Центры внуков"
- **ROI:** 8.3x ⭐ HIGHEST

#### TAB 3: Self-Confident Youth (18%)
- **Demographics:** 18-30 лет | Доход 50-300k₽/мес | Город 85% | Соцсети активен
- **Financial Impact:**
  - Средний убыток: 250k₽ (медиана)
  - Восстановление: 12%
  - Кумулятивный ущерб: 123.7B₽
- **Risk Factors:** Переоценка навыков | FOMO | Много личной инфо в интернете
- **Attack Vectors:** Крипто-инвестиции в Telegram, вирусы (пиратский контент), deepfake видео, QR-фишинг
- **Protection:** Peer-to-peer образование (TikTok), лимиты (50k₽/день), крипто-курсы в вузах
- **ROI:** 6.8x

#### TAB 4: In Credit Trap (12%)
- **Demographics:** Смешанный возраст | Доход 20-80k₽/мес | Провинции 60% | Микрокредиты + коллекторы
- **Financial Impact:**
  - Средний убыток: 400k₽ (медиана)
  - Восстановление: 3%
  - Кумулятивный ущерб: 178.3B₽ ⚠️ HIGHEST CUMULATIVE
  - Социальный коллапс: 12% становятся бездомными
- **Risk Factors:** Финансовое отчаяние | Низкий критицизм | Манипулируемость
- **Attack Vectors:** "Чудо-заработок" (WFH), микрокредиты в Telegram, пирамиды, давление коллекторов
- **Protection:** Финконсультант горячая линия, реальные микрокредиты (15-20% APR), психологическая поддержка, судебная помощь
- **ROI:** 4.2x (LOW but HIGH social value)

#### TAB 5: Unintentional Victim (10%)
- **Demographics:** Любой возраст/доход/образование
- **Financial Impact:**
  - Убыток: переменный
  - Восстановление: 18%
- **Characteristic:** Жертва вируса (не социнженерия)
- **Protection:** Обновленный антивирус, облачные резервы, изоляция устройства
- **ROI:** 9.1x ⭐ HIGHEST

**Profile Comparison Feature:**
- Add checkbox for each profile (drag/drop to compare)
- Shows side-by-side metrics in a comparison table
- Highlights key differences in ROI, vulnerability, demographics

---

### SECTION 4: FINANCIAL SCENARIOS (3 TABS: A / B / C)

**Tab Navigation:**
```
[Scenario A: Quick Wins (6 мес)]  [Scenario B: Comprehensive ⭐] [Scenario C: Transformational]
```

#### SCENARIO A: Quick Wins (6 months)
- **Investment:** 2.9B₽
  - 2FA: 1.2B
  - Triage system: 0.8B
  - Education: 0.6B
  - Hotline: 0.3B
- **Prevented losses:** 68.4B₽
- **ROI: 23.6x** 🏆 FASTEST
- **Breakeven:** 1.5 months
- **Success probability:** 95%
- **Visual:** Investment waterfall chart → ROI gauge (gold highlight at 23.6x)
- **Risks:** User resistance (30%), hacker adaptation (40%), data leak (5%)

#### SCENARIO B: Comprehensive (12 months) ⭐ RECOMMENDED
- **Investment:** 8.5B₽
  - 2FA + biometrics: 2.5B
  - Triage expanded: 1.2B
  - AI filters in messengers: 1.8B
  - Education multi-channel: 1.5B
  - Hotline expanded: 0.9B
  - Microloans: 0.6B
- **Prevented losses:** 200B₽
- **ROI: 12.7x** 💡 BALANCED
- **Breakeven:** 8 months
- **Success probability:** 85%
- **Quarterly KPI trajectory:**
  - Q4 2025: Contact 36.7%, Detection 48h, 2FA 35%, Trust 62%
  - Q1 2026: Contact 35.5%, Detection 36h, 2FA 45%, Trust 65%
  - Q2 2026: Contact 33.2%, Detection 24h, 2FA 58%, Trust 68%
  - Q3 2026: Contact 30.1%, Detection 12h, 2FA 70%, Trust 72%
  - Q4 2026: Contact 27.3%, Detection 4h, 2FA 82%, Trust 76%
- **Visual:** Cumulative ROI line chart (months 1-12), showing breakeven at month 8
- **Risks:** Technical failure (15%), platform resistance (20%), budget overrun (25%)

#### SCENARIO C: Transformational (18-24 months)
- **Investment:** 10.5B₽
  - All of B: 8.5B
  - CBDC integration: 1.2B
  - Blockchain: 0.5B
  - Quantum crypto: 0.2B
  - Biometric passport: 0.1B
- **Prevented losses:** 300B₽
- **ROI: 10.0x** 🚀 STRATEGIC
- **Contact rate:** 36.7% → 18.5% (nearly 2x reduction)
- **Success probability:** 70% (technical complexity)
- **Benefits:** Tech leadership, BRICS export, sanctions resilience
- **Visual:** Risk matrix (complexity vs probability), strategic value prop
- **Risks:** CBDC failure (30%), political pressure, budget overrun (40%), delays (60%)

**Shared Scenario Features:**
- Comparison slider: drag to compare metrics across A/B/C
- Sensitivity analysis: "What if investment is ±20%?" dropdown
- Key metrics tracker: contact rate, detection speed, recovery rate, 2FA adoption, trust level
- Recommendation banner: "We recommend Scenario B for maximum impact" (highlight green)

---

## ADVANCED FEATURES (OPTIONAL PHASE 2)

### Geographic Heatmap
- Russia map showing victim concentration
- Urban areas (Moscow, SPb): 75% concentration
- Color scale: light (low) → dark red (high)
- Click region → detailed breakdown by age, income, channel

### ML Model Explainability
**Feature Importance Bar Chart:**
- Security Awareness: 28.47% (dominates)
- Digital Literacy: 21.56%
- Bank Experience: 18.34%
- Device Security: 15.42%
- Bank Trust: 11.02%
- SMS Check Habit: 3.19%
- Other: 2.00%

**Confusion Matrix Display:**
- True Positives: 13,275 (88.5% recall)
- False Negatives: 1,725
- False Positives: 1,650
- True Negatives: 10,350
- Accuracy: 88.8% (F1-Score)

### Recovery Dashboard
- Total recovery: 14.6B₽ (2025) → target 43.5B₽ (2027)
- Recovery rate by profile: Elderly 22%, Professional 8%, Youth 12%, Credit Trap 3%, Unintentional 18%
- Success stories: 3-5 anonymized case studies (\\\"Recovered 250k₽ within 5 days\\\")

---

## INTERACTIVE FEATURES CHECKLIST

- [ ] **Hover tooltips** on all charts (show exact numbers, percentages, explanation text)
- [ ] **Click to expand/collapse** profile cards
- [ ] **Drag to compare** scenarios (slider between A/B/C)
- [ ] **Dark/Light mode toggle** (button in top-right)
- [ ] **Mobile responsive** (stack vertically on mobile, grid on desktop)
- [ ] **Smooth animations** (0.3s transitions between states, fade-in on load)
- [ ] **Keyboard navigation** (Tab through tabs, arrow keys in profiles)
- [ ] **Search/filter** (search for fraud channel or profile type, narrows view)
- [ ] **Download as PDF** (button to export dashboard as report)
- [ ] **Live data simulation** (data refreshes every 5 seconds, showing real-time updates)

---

## TECHNICAL STACK (SINGLE HTML FILE)

**Libraries to include (via CDN):**
- **Chart.js** (charts, Sankey): `<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/3.9.1/chart.min.js"></script>`
- **Plotly.js** (alternative for Sankey): `<script src="https://cdn.plot.ly/plotly-latest.min.js"></script>`
- **AOS (Animate On Scroll)**: `<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/aos/2.3.4/aos.css">`
- **Tailwind CSS** (styling via CDN): `<script src="https://cdn.tailwindcss.com"></script>`

**Structure:**
```html
<!DOCTYPE html>
<html lang="ru">
<head>
    <!-- Meta tags, fonts, CDN links -->
</head>
<body>
    <header><!-- KPI Stats Cards --></header>
    
    <section><!-- Fraud Channels: Sankey + Table --></section>
    
    <section><!-- Victim Profiles: 5 Tabs --></section>
    
    <section><!-- Financial Scenarios: 3 Tabs --></section>
    
    <footer><!-- © 2026 ЦБ РФ | Last updated --></footer>
    
    <script>
        // Data (hardcoded for MVP)
        const fraudData = {
            channels: [...],
            profiles: [...],
            scenarios: [...],
            kpis: [...]
        };
        
        // Chart initialization
        // Event listeners
        // Interactive logic
    </script>
</body>
</html>
```

**Data Format (JavaScript objects):**
```javascript
const channels = [
    { name: "Телефон/СМС", attempts: 54.6, penetration: 83.1, conversion: 27.5, avgLoss: 42700, trend: 18 },
    { name: "Мессенджер", attempts: 16.1, penetration: 28.7, conversion: 35.2, avgLoss: 87500, trend: 22 },
    // ...
];

const profiles = [
    { 
        id: 1, 
        name: "Напряженный профессионал", 
        percent: 35, 
        age: "25-44", 
        income: "150-400k", 
        avgLoss: 85000, 
        recovery: 8, 
        roi: 5.2,
        color: "#FF8C00"
    },
    // ...
];

const scenarios = [
    {
        id: "A",
        name: "Quick Wins",
        months: 6,
        investment: 2.9,
        prevented: 68.4,
        roi: 23.6,
        breakeven: 1.5,
        probability: 95,
        kpis: {
            contact: [36.7, 33.2],
            detection: [48, 24],
            twofa: [35, 58],
            trust: [62, 68]
        }
    },
    // ...
];
```

---

## DESIGN MOCKUP TEXT (Copy-paste friendly)

**Header Section:**
```
┌────────────────────────────────────────────────────────────────┐
│ 🛡️  AntiScam Dashboard | ЦБ РФ — Анализ финансового мошенничества
└────────────────────────────────────────────────────────────────┘

┌──────────────┐ ┌──────────────┐ ┌──────────────┐ ┌──────────────┐ ┌──────────────┐ ┌──────────────┐
│  Жертвы      │ │  Убытки      │ │  Контакт     │ │  Восстан.    │ │  Скорость    │ │  2FA         │
│  7.1M        │ │  98.4B₽      │ │  36.7%       │ │  14.6B₽      │ │  48 часов    │ │  35%         │
│  ↑ +37% 2024 │ │  ↑ +35% 2024 │ │  ↑ +23% 2024 │ │  ↑ +3% 2024  │ │  (Q4 2025)   │ │  (внедр.)    │
└──────────────┘ └──────────────┘ └──────────────┘ └──────────────┘ └──────────────┘ └──────────────┘
```

---

## ACCEPTANCE CRITERIA

- ✅ Dashboard loads in < 2 seconds
- ✅ All 6 KPI cards display with correct 2025 data
- ✅ Sankey diagram is interactive (hover shows tooltips, click expands)
- ✅ All 5 victim profile tabs functional with correct statistics
- ✅ Scenario A/B/C tabs show correct KPI trajectories
- ✅ Comparison slider works (drag between A/B/C)
- ✅ Mobile responsive (looks good on phone, tablet, desktop)
- ✅ Dark mode toggle works
- ✅ Charts animate smoothly on load
- ✅ No console errors
- ✅ Deployed to GitHub Pages / Vercel / Render (public URL)

---

## DELIVERY TIMELINE

**Phase 1 (2 days):**
- HTML skeleton + header with KPI cards
- Sankey diagram (fraud channels)
- Basic styling (dark theme, professional colors)

**Phase 2 (2 days):**
- 5 victim profile tabs (content + styling)
- Victim profile comparison widget
- Responsive design

**Phase 3 (2 days):**
- 3 financial scenario tabs
- Scenario comparison slider
- KPI trajectory charts

**Phase 4 (1 day):**
- Dark/light mode toggle
- Mobile optimization
- Deploy to public URL
- Polish animations

---

## BUSINESS PITCH

**This dashboard is:**
✅ Data-driven (based on ЦБ РФ research with N=468K victims)
✅ Interactive (everyone can explore their profile/scenario)
✅ Professional (ready to show to banks, МВД, decision-makers)
✅ Actionable (clear ROI numbers, scenario comparisons)
✅ Beautiful (modern design, smooth animations)

**Expected impact:**
- Banks: Clear visibility into fraud risk and ROI of protection measures
- Regulators: Data to justify fraud prevention programs
- Public: Understand their vulnerability profile and protection strategies

---

## BONUS: ANIMATION IDEAS

- 🎬 **Fade-in on scroll:** KPI cards fade in as user scrolls down
- 🎬 **Sankey flow animation:** Flows animate when page loads (1s duration)
- 🎬 **Counter animation:** KPI numbers count up from 0 (e.g., 0 → 7.1M over 1s)
- 🎬 **Hover glow:** Cards glow on hover (box-shadow effect)
- 🎬 **Tab switching:** Smooth fade between profile tabs (0.3s)
- 🎬 **Scenario slider:** Smooth number transitions when slider moves

Good luck! 🚀
