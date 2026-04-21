# 🧠 Mug Up Master

> A hardcore browser-based memorization platform for competitive exam prep — sequential learning, brutal restart rules, checkpoint system, and zero server required.

---

## 📖 Description

**Mug Up Master** is a single-file, zero-dependency study tool built for students preparing for competitive exams like SSC, UPSC, and school-level tests. It covers **4 subjects** across **19 categories** — Maths, Science, SSC GK, and English — with a strict sequential learning model: get one question wrong and you restart from Q1. No shortcuts, no skipping. Complete every question in an unbroken run to unlock **Infinite Mode**, a randomised practice pool drawn from only your finished categories. Progress can be exported to a JSON file and re-imported on any device to continue right where you left off.

---

## ✨ Features

| Feature | Details |
|---|---|
| 📚 **4 Subjects** | Math, Science, SSC GK, English |
| 🗂️ **19 Categories** | Squares, Cubes, Tables, Primes, SI Units, Elements, History, Geography, Idioms, Tenses, Voice, Spellings & more |
| 🔁 **Sequential Learning** | Questions served in strict order — no skipping |
| ❌ **Wrong = Restart** | One wrong answer shows the correct one, then resets to Q1 |
| ✅ **Complete to Unlock** | Categories unlock Infinite Mode only after a full clean run |
| ♾️ **Infinite Mode** | Random questions from all unlocked categories with streak tracking |
| 🏁 **Checkpoint System** | Categories with 50+ questions are split into checkpoints of 50 |
| 💾 **Export / Import** | Save progress as `.json`, reload on any device to resume |
| 🌙 **Dark / Light Mode** | Toggle between themes, preference saved to `localStorage` |
| 🎯 **Scope Cursor** | Custom crosshair cursor that changes colour per active module |
| 🔒 **Locked Navigation** | Inside a module, only the Home button exits — no accidental back-navigation |
| 📱 **Responsive** | Works on desktop and mobile (cursor animation auto-disables on touch) |
| ⚡ **Zero Dependencies** | Pure HTML + CSS + Vanilla JS — no frameworks, no build step, no server |

---

## 🚀 Getting Started

### Option 1 — Open directly
Just download `mug-up-master.html` and open it in any modern browser. That's it.

```bash
# Clone the repo
git clone https://github.com/your-username/mug-up-master.git
cd mug-up-master

# Open in browser
open mug-up-master.html        # macOS
start mug-up-master.html       # Windows
xdg-open mug-up-master.html    # Linux
```

### Option 2 — Serve locally (optional)
```bash
# Python 3
python -m http.server 8080

# Node (npx)
npx serve .
```
Then visit `http://localhost:8080`.

> No npm install, no build process — the entire app is one `.html` file.

---

## 🗺️ Subject Map

### 🧮 Math Master
- **Squares** — 1² to 25²
- **Cubes** — 1³ to 15³
- **Tables 1–20** — full multiplication tables (200 questions, split into 4 checkpoints of 50)
- **Prime Numbers** — all 25 primes up to 100
- **Fractions / Decimal / %** — conversions both ways
- **Basic Formulas** — area, volume, speed, interest, and more

### 🔬 Science Master
- **SI Units** — 7 base units + derived units
- **Physics Formulas** — force, work, power, momentum, Newton's laws
- **Periodic Table 1–20** — symbol → name
- **Biology Systems** — digestive, nervous, circulatory, skeletal & more

### 🌍 SSC Master
- **History Events** — key dates from 1526 to Independence
- **States & Capitals** — 20 Indian states
- **Rivers & Mountains** — major Indian geography
- **Civics & Constitution** — articles, amendments, Parliament structure

### 📝 English Master
- **Idioms & Phrases** — 15 common expressions with meanings
- **Grammar: Tenses** — all 12 tenses with structure patterns
- **Active / Passive Voice** — conversion rules across all tenses
- **Common Spellings** — 15 frequently misspelled words

---

## 💾 Save & Resume

Progress is **not** auto-saved (no backend). Use the built-in **Save / Load** system:

1. Click **Save / Load** in the top-right nav bar
2. Click **Export Progress** — downloads `mug-up-progress-YYYY-MM-DD.json`
3. Next session: click **Save / Load → Import Save File**
4. Your completed categories and checkpoints restore instantly

The JSON file is human-readable and portable — works across browsers and devices.

---

## 🏗️ Architecture

```
mug-up-master.html
│
├── <style>           CSS — theme tokens, screen system, all components
├── <body>
│   ├── #nav-bar      Floating nav: Save/Load · Help · Theme toggle
│   ├── #home         Landing screen with module cards + save/load banner
│   ├── #module-view  Module shells (math / science / ssc / english)
│   │   ├── .mod-header   Sticky header with back button
│   │   ├── .mod-sidebar  Category list (desktop only)
│   │   └── .mod-content  Dynamic content area
│   ├── #help         Scrollable help screen
│   └── modals / toast
│
└── <script>
    ├── Theme         Toggle + localStorage restore
    ├── DATA          All question generators (pure functions)
    ├── State         completed{}, learnState, infState
    ├── Navigation    showScreen(), history.pushState, popstate handler
    ├── Learn Flow    renderLearnView(), checkpoint system, submitLearn()
    ├── Infinite Mode renderInfiniteView(), submitInf()
    ├── Export/Import doExport(), doImport(), modal logic
    ├── Animations    Web Animations API — cards, slides, feedback
    └── Cursor        Scope/crosshair cursor with module accent colours
```

---

## ⚙️ How the Learning Engine Works

```
User clicks category
        │
        ▼
Does it have > 50 questions?
   YES → Show Checkpoint Picker → User picks a chunk of 50
   NO  → Load all questions directly
        │
        ▼
Questions served one by one in order
        │
   ┌────┴────┐
CORRECT    WRONG
   │          │
   │     Show answer
   │     Restart idx = 0
   ▼          │
Next Q ◄──────┘
   │
All done?
   YES → Mark category/chunk complete → Unlock Infinite Mode
   NO  → Continue
```

---

## 🎨 Design System

| Token | Dark | Light |
|---|---|---|
| Background | `#090b12` | `#f4f5fb` |
| Surface | `#111422` | `#ffffff` |
| Math accent | `#f5a623` | same |
| Science accent | `#00d4a0` | same |
| SSC accent | `#f53b3b` | same |
| English accent | `#a855f7` | same |

**Fonts:** Clash Display (headings) · Outfit (body) · JetBrains Mono (questions/code)  
**Animations:** Web Animations API (no CSS animation library)  
**No external JS** — Google Fonts is the only external resource

---

## 📋 Browser Support

| Browser | Support |
|---|---|
| Chrome 90+ | ✅ Full |
| Firefox 88+ | ✅ Full |
| Safari 14+ | ✅ Full |
| Edge 90+ | ✅ Full |
| Mobile Safari / Chrome | ✅ (cursor auto-disabled) |

---

## 🤝 Contributing

Contributions are welcome! Here are some ideas:

- **Add more questions** — extend any `gen()` function in the `DATA` object
- **New category** — add a new entry to any module's `categories` array
- **New module** — duplicate the HTML shell pattern and add a key to `DATA`
- **Bug fixes / UX improvements** — open an issue or PR

```js
// Example: adding a new category to Math
{ id: 'roots', label: 'Square Roots', icon: '√',
  gen: () => Array.from({length:15}, (_,i) => ({
    q: `√${(i+2)**2} = ?`,
    a: `${i+2}`,
    hint: `${i+2} × ${i+2} = ${(i+2)**2}`
  }))
}
```

---

## 📄 License

MIT — free to use, modify, and distribute. A credit/star is appreciated but not required.

---

## 🙏 Acknowledgements

Built as a personal study tool for competitive exam preparation. Inspired by spaced repetition principles and the philosophy that **struggling to recall is what builds memory** — hence the restart-on-wrong mechanic.

---

<p align="center">Made with ☕ and frustration at forgetting things · <strong>Mug Up Master</strong></p>
