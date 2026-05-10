# 📱 T3373 — Introduction to Android Programming
## Complete Study Guide

> **Course:** T3373 · **Level:** 3 · **Credits:** 2  
> **Pre-requisite:** Java SE  
> **Books:** Head First Android Development · Hello Android · Beginning Android 4

---

## 📚 Study Documents

| # | Topic | Hours | File |
|---|-------|-------|------|
| 1 | Mobile Application Development & Frameworks | 6 | `01_Mobile_App_Frameworks.md` |
| 2 | Android Architecture, SDK, IDE & Build Process | 6 | `02_Android_Architecture.md` |
| 3 | Building Blocks, Activity Lifecycle & LogCat | 4 | `03_Activity_Lifecycle.md` |
| 4 | Creating UI with Activity & Views | 10 | `04_Views_UI.md` |
| 5 | Layouts | 4 | `05_Layouts.md` |

---

## 🗂️ Quick Cheat Sheet

### The Android Layer Stack (bottom → top)
```
[ Your App ]
    ↑
[ Application Framework (Activity Manager, View System…) ]
    ↑
[ Android Runtime (ART) + Core Libraries ]
    ↑
[ C/C++ Libraries (SQLite, WebKit, OpenGL…) ]
    ↑
[ Linux Kernel (drivers, power, security) ]
```

### Activity Lifecycle (one-liner)
`onCreate → onStart → onResume → [RUNNING] → onPause → onStop → onDestroy`

### Key View Types
| Widget | XML Tag | Purpose |
|--------|---------|---------|
| Label | `<TextView>` | Display text |
| Input | `<EditText>` | User text input |
| Button | `<Button>` | Tap action |
| Checkbox | `<CheckBox>` | Multi-select |
| Radio | `<RadioButton>` inside `<RadioGroup>` | Single-select |
| Slider | `<SeekBar>` | Drag for value |
| Stars | `<RatingBar>` | Star rating |

### Key Layout Types
| Layout | Behaviour |
|--------|-----------|
| `LinearLayout` | Arranges children in a single row or column |
| `RelativeLayout` | Positions children relative to each other or parent |
| `FrameLayout` | Stacks children on top of each other |
| `GridLayout` | Places children in a rows-and-columns grid |
| `ScrollView` | Wraps content to make it scrollable |

---

## 📝 Evaluation Breakdown
- **Quiz** — Short factual questions on each topic
- **Assignments** — Coding & written tasks
- **Writing Assignments** — Theory explanations
- **Practical Exam** — Build a small Android app
