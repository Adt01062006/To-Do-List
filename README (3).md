# Taskflow AI — Advanced Todo App

A beautifully designed, AI-powered task management app built with vanilla HTML, CSS, and JavaScript. No frameworks, no dependencies — just a single `.html` file you can open anywhere.

---

## ✨ Features

### Core Task Management
- **Add tasks** with category, priority, and due date
- **Edit tasks** via a clean modal — update text, notes, category, priority, due date, and status
- **Delete & duplicate** tasks with one click
- **Mark tasks complete** with a satisfying checkbox animation
- **Drag and drop** to reorder tasks manually

### Filters & Search
- Filter by **All / Active / Done / Overdue**
- Filter by **category** using pill tabs (Personal, Work, Study, Health, Other)
- **Live search** across task titles and notes
- **Sort** by newest, priority, due date, or A→Z

### Stats & Progress
- Real-time stats bar — Total, Active, Done, Overdue counts
- **Progress bar** showing overall completion percentage

### Bulk Actions
- Select multiple tasks and **bulk complete** or **bulk delete**

### AI Features (Claude API)
- **✦ AI Task Suggestions** — describe your goal in plain English and Claude auto-generates 3–5 specific, actionable tasks with category, priority, and due date already filled in
- **✦ AI Subtask Breakdown** — open any task's edit modal and let Claude break it into step-by-step subtasks you can check off one by one
- Add AI-suggested tasks one at a time or all at once

### UI & Experience
- **Dark mode** toggle, saved to localStorage
- **Toast notifications** for every action
- Responsive design — works on mobile and desktop
- Warm parchment color palette with subtle dot-grid texture
- Fraunces serif display font + DM Mono for data + Outfit for UI
- Smooth animations on task add, modal open, and hover states

---

## 🚀 Getting Started

### 1. Clone the repo

```bash
git clone https://github.com/Adt01062006/taskflow-ai.git
cd taskflow-ai
```

### 2. Open the app

Just open `index.html` in your browser — no build step, no server needed.

```bash
open index.html
```

### 3. Set up the AI features (optional)

The app calls the **Anthropic Claude API** directly from the browser. To enable AI features you need an Anthropic API key.

> **Note:** For production use, proxy API calls through your own backend so your key is never exposed in the browser.

---

## 🤖 AI Backend — How It Works

The app uses the Anthropic Messages API (`claude-sonnet-4-20250514`) with two AI functions:

### AI Task Suggestions
Type a goal like *"Prepare for the client presentation next Friday"* and Claude returns a JSON array of tasks:

```json
[
  {
    "text": "Outline presentation structure and key talking points",
    "category": "work",
    "priority": "high",
    "due": "2026-05-14",
    "note": "Focus on the problem, solution, and results sections"
  }
]
```

These are rendered as suggestion cards. You can add them individually or all at once.

### AI Subtask Generator
Open any task's edit modal and click **✦ Break into subtasks with AI**. Claude breaks the task into 3–6 concrete subtasks:

```json
[
  { "text": "Book the meeting room", "done": false },
  { "text": "Send calendar invite to all stakeholders", "done": false },
  { "text": "Prepare slide deck", "done": false }
]
```

Subtasks are stored with the task and shown as checkboxes in the modal, with a count (`2/5 subtasks`) on the task card.

---

## 🗂 Project Structure

```
taskflow-ai/
├── index.html       # The entire app — HTML, CSS, and JS in one file
└── README.md
```

The app is intentionally a single file. All state is managed in memory and persisted to `localStorage`.

---

## 💾 Data Storage

Tasks are saved to `localStorage` under the key `tf_tasks`. Each task object looks like this:

```json
{
  "id": 1716123456789,
  "text": "Review quarterly report",
  "category": "work",
  "priority": "high",
  "due": "2026-05-20",
  "note": "Focus on Q2 projections",
  "done": false,
  "createdAt": "2026-05-16T10:30:00.000Z",
  "subtasks": [
    { "id": 1716123456790, "text": "Read the executive summary", "done": true },
    { "id": 1716123456791, "text": "Annotate key figures", "done": false }
  ]
}
```

You can export all tasks as a JSON file using the **📤 Export** button.

---

## 🎨 Design System

| Token | Value | Usage |
|---|---|---|
| `--bg` | `#f5f0e8` | Page background |
| `--surface` | `#ffffff` | Cards and inputs |
| `--accent` | `#c84b2f` | Primary action color |
| `--accent3` | `#2f6bc8` | Active state |
| `--green` | `#2a7a4b` | Completed state |
| `--yellow` | `#c8960f` | Overdue state |
| `--purple` | `#6b3fc8` | AI features |

**Fonts:** Fraunces (display) · DM Mono (data/labels) · Outfit (UI)

---

## 🧠 Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Vanilla HTML5, CSS3, JavaScript (ES2020+) |
| Storage | Browser `localStorage` |
| AI | Anthropic Claude API (`claude-sonnet-4-20250514`) |
| Fonts | Google Fonts |
| Build | None — single `.html` file |

---

## 📋 Task Categories

| Category | Emoji | Color |
|---|---|---|
| Personal | 👤 | Purple |
| Work | 💼 | Blue |
| Study | 📚 | Red-orange |
| Health | 💚 | Green |
| Other | 📌 | Grey |

---

## ⚡ Keyboard Shortcuts

| Key | Action |
|---|---|
| `Enter` (in task input) | Add task |
| `Enter` (in AI input) | Trigger AI suggestions |
| `Esc` | Close modal |

---

## 🔒 Privacy & Security

- All task data stays **in your browser** — nothing is sent to any server except the AI prompt text when you use the AI features.
- AI prompt text (your goal description or task title) is sent to Anthropic's API to generate suggestions.
- No user accounts, no tracking, no analytics.

---

## 📄 License

MIT — use it, modify it, ship it.

---

## 🙋 Author

Built by **[Aditi Dubey]**  
GitHub: [@Adt01062006](https://github.com/Adt01062006)
