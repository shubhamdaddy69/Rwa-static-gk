# SSC Scholars — Mock Test Website

A complete, self-hosted mock test platform for GitHub Pages.

## 📁 Folder Structure

```
your-repo/
├── index.html          ← Mock selector (home page)
├── attempt.html        ← Test-taking interface
├── performance.html    ← Performance tracker dashboard
└── mocks/
    ├── mock1.json      ← Your mock data files
    ├── mock2.json
    ├── mock3.json
    └── ...up to mock50.json
```

---

## 🚀 Setup on GitHub Pages

1. Create a GitHub repository (e.g., `my-ssc-mocks`)
2. Upload ALL files from this folder keeping the same structure
3. Go to **Settings → Pages → Source → Deploy from branch (main)**
4. Your site will be live at: `https://yourusername.github.io/my-ssc-mocks/`

---

## ➕ Adding Your 50 Mock Files

Each mock is a `.json` file placed in the `mocks/` folder.

### JSON Format:

```json
{
  "title": "Mock 1 — SSC CGL Tier I",
  "duration_minutes": 60,
  "sections": [
    {
      "name": "General Intelligence & Reasoning",
      "positive_marks": 2,
      "negative_marks": 0.5,
      "questions": [
        {
          "question": "Your question text here (HTML supported)",
          "options": ["Option A", "Option B", "Option C", "Option D"],
          "correct_option": 0,
          "explanation": "Explanation for the correct answer (optional)"
        }
      ]
    }
  ]
}
```

- `correct_option` is **0-indexed** (0 = A, 1 = B, 2 = C, 3 = D)
- `question` and `options` support HTML (bold, images, etc.)
- Name files exactly: `mock1.json`, `mock2.json`, ..., `mock50.json`

---

## ⚙️ Configuring Active Mocks (index.html)

Open `index.html` and find the `MOCKS_CONFIG` array:

```javascript
const MOCKS_CONFIG = [
  { id: 1,  phase: 1, active: true,  file: 'mocks/mock1.json'  },
  { id: 2,  phase: 1, active: true,  file: 'mocks/mock2.json'  },
  { id: 12, phase: 2, active: false, file: 'mocks/mock12.json' },
  // ...
];
```

- Set `active: true` to make a mock available
- Set `active: false` to show it as "Coming Soon"
- Change `phase` to group mocks into phases

---

## ✨ Features

### Test Interface (`attempt.html`)
- ⏱️ Countdown timer (auto-submit when time ends)
- 📋 Question palette (sidebar) with color-coded status:
  - 🟢 **Green** = Answered
  - 🟠 **Orange** = Marked for Review
  - 🔵 **Blue tint** = Visited but not answered
  - ⬛ **Dark** = Not visited
- 🔖 Mark for Review button
- ➕/➖ Positive & negative marking per section
- 📊 Section filter (attempt by section)
- 📝 Review mode after submission with correct answers + explanations
- 💾 Results saved to browser localStorage

### Performance Dashboard (`performance.html`)
- 📈 Score trend chart (line graph across all attempts)
- 📊 Accuracy bar chart per mock
- 🗂️ Section-wise analysis (correct/wrong/skipped %)
- 📜 Complete attempt history table with ratings
- 🧮 Overview stats: Best score, Avg score, Accuracy, Improvement

---

## 🎨 Customization

To change the **Telegram link**, search for `t.me/thesscscholarsofficial` and replace it.

To change the **exam name** (CGL • CHSL etc.), edit the subtitle in `index.html`:
```html
<div class="subtitle">Mock Test Series — CGL • CHSL • CPO • STENO</div>
```

---

## 📝 Notes

- All performance data is stored in the **browser's localStorage** (per device)
- No backend/database needed — fully static site
- Works on mobile too (responsive design)
- Images in questions: host image on GitHub and use the raw URL in `<img>` tags
