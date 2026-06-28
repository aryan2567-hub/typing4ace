# TypeFlow — Typing Practice Website

A clean, fully client-side typing practice app with real-time WPM tracking, accuracy scoring, mistake highlighting, a progress chart, session history, dark mode, and multiple difficulty levels. No server required — just open `index.html` in a browser.

---

## Features

- **Live WPM, accuracy, and mistake counter** — updates on every keystroke
- **Mistake highlighting** — wrong characters turn red with a background tint; correct ones turn green
- **Difficulty selector** — Easy, Medium, and Hard, each with realistic paragraphs using capital letters, commas, apostrophes, and punctuation
- **Timer modes** — 15s, 30s, 60s, 2 minutes, or No limit; timer turns orange under 10s and red under 5s
- **WPM progress chart** — line graph powered by Chart.js, updates after every session
- **Session history table** — last 20 sessions saved in `localStorage` (persists across browser tabs and refreshes)
- **Result panel** — final WPM, accuracy, mistakes, and time when you finish or time runs out
- **Dark mode** — toggle in the top-right corner; preference saved across visits
- **No dependencies to install** — Chart.js and Google Fonts load from CDN; everything else is vanilla HTML, CSS, and JS

---

## Project Structure

```
typing-practice/
├── index.html    — page structure and layout
├── style.css     — all styling including dark mode tokens
├── script.js     — game logic, timer, stats, history, chart
└── README.md     — this file
```

---

## Getting Started

### Run locally

1. Download or unzip the project folder
2. Double-click `index.html` — it opens directly in your browser
3. Click the text area and start typing

No build step, no Node.js, no server needed.

### Publish online (free)

**Netlify Drop** (30 seconds):
1. Go to [netlify.com/drop](https://netlify.com/drop)
2. Drag and drop the entire project folder
3. You get a live public URL instantly

**GitHub Pages**:
1. Push the folder to a GitHub repository
2. Go to Settings → Pages → Source → Deploy from branch (`main`, `/ root`)
3. Your site is live at `https://yourusername.github.io/repo-name`

**Vercel**:
1. Import the GitHub repo at [vercel.com](https://vercel.com)
2. No configuration needed — it detects a static site automatically

---

## How to Use

| Action | Description |
|---|---|
| Click the text area | Focuses the input and starts the session |
| Type the displayed text | Green = correct, red = wrong |
| Backspace | Delete the last character |
| New text button | Loads a fresh sentence and resets stats |
| Difficulty pills | Switch between Easy / Medium / Hard |
| Timer pills | Choose 15s, 30s, 60s, 2m, or No limit |
| Dark mode toggle | Top-right corner, moon/sun icon |
| Clear history | Removes all saved sessions from storage |

---

## Difficulty Levels

| Level | Description | Example |
|---|---|---|
| Easy | Short sentences, common words, simple punctuation | "The sun rose slowly over the hills, casting a warm golden light." |
| Medium | Longer paragraphs, dialogue, complex sentences | "The conference room fell silent when Marcus entered." |
| Hard | Technical, academic, and philosophical language | "Quantum entanglement, Einstein's so-called 'spooky action at a distance'…" |

Each level has 6 unique paragraphs that are selected randomly.

---

## Customisation

### Add your own text

Open `script.js` and find the `TEXTS` object near the top. Add new strings to any difficulty array:

```js
const TEXTS = {
  easy: [
    "Your custom sentence goes here.",
    // ... existing sentences
  ],
  medium: [ /* ... */ ],
  hard:   [ /* ... */ ]
};
```

### Change the colour scheme

Open `style.css` and edit the CSS variables in the `:root` block (light mode) or `[data-theme="dark"]` block (dark mode):

```css
:root {
  --accent: #3b7df8;   /* blue highlight colour */
  --correct: #1d8348;  /* green for correct characters */
  --wrong:   #c0392b;  /* red for wrong characters */
}
```

### Add a new timer option

In `index.html`, add a pill button inside `#timer-group`:

```html
<button class="pill" data-time="180">3m</button>
```

The `data-time` value is in seconds. Use `0` for no limit.

### Change the number of saved sessions

In `script.js`, find this line and change `20` to your preferred limit:

```js
if (history.length > 20) history = history.slice(0, 20);
```

---

## Browser Support

Works in all modern browsers — Chrome, Firefox, Safari, and Edge. Requires JavaScript enabled. Internet connection needed only on first load (to fetch Chart.js and fonts from CDN); after that it works offline if the browser has cached those resources.

---

## Tech Stack

| Technology | Purpose |
|---|---|
| HTML5 | Page structure |
| CSS3 (custom properties) | Styling and dark mode |
| Vanilla JavaScript (ES6+) | Game logic, timer, localStorage |
| [Chart.js 4](https://www.chartjs.org/) | WPM progress line chart |
| [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) | Monospace font for typing display |
| [Inter](https://fonts.google.com/specimen/Inter) | UI font |

---

## Roadmap (ideas for next steps)

- [ ] Keyboard heatmap showing which keys you miss most
- [ ] Sound effects on correct / wrong keypress
- [ ] Custom text paste mode
- [ ] Multiplayer race mode (requires a backend)
- [ ] Export history as CSV
- [ ] More language packs (Hindi, Spanish, French)

---

## License

Free to use, modify, and deploy for personal or educational projects.
