# Habit Tracker — Spec (v1.1)

## Goal
Build a minimalist, “Stack-like” habit tracker that is fast, bold, elegant, and usable daily. Local-first. Real-time insights. A coach that keeps me on track.

## Product Principles (Non-negotiables)
- Minimalist, bold, clean. No visual noise.
- Solid colors only. No gradients. No glows.
- Typography is strong and readable. Clear hierarchy.
- Everything updates immediately when I check/uncheck.
- Mobile + desktop friendly (Chromebook included).
- Local-first: works without internet once loaded.

## Layout (Stack-like structure)
Single page with two primary sections:

### A) Operations (Top section)
- Lives in the upper part of the screen (slightly under half).
- Contains:
  - Weekly check-in grid (default)
  - Monthly check-in grid (toggle)
  - Add habit
  - Export
- The grid itself can scroll horizontally if needed.

### B) Insights / Coach (Bottom section)
- Lives in the lower part of the screen (about half).
- Contains:
  - Analytics cards (rings / circles)
  - Neglected habits list
  - Coach panel (real-time insights)

## Navigation & Expand Behavior (critical)
- Each section is scrollable *inside its own container* (in-place scrolling).
- Each section can be expanded to “full view”:
  - Click section header OR an “Expand” icon/button.
  - Expanded mode takes over the screen (fullscreen modal or full-height panel).
  - Expanded mode has a “Close” / “Back” control.
- When expanded, that section uses the full viewport and its content remains scrollable.

## UI System
### Colors (solid palette, wider range)
- Use a controlled palette of solid accent colors for distinction:
  - Purple, Blue, Teal, Green, Amber, Red, Pink, Slate
- Accents only: backgrounds remain dark/neutral.
- Don’t use gradients anywhere.
- Only 1–2 accent colors visible at a time per component.

### Components must feel “Stack-like”
- Cards: clean, rounded, minimal borders.
- Spacing: generous, consistent.
- Buttons: solid fills, bold text, no fancy effects.
- Badges (must be better):
  - Rounded pill
  - Solid fill
  - High contrast text
  - Clear meaning (OK / Warning / Risk)
  - Example badge states:
    - ON TRACK (green)
    - SLIPPING (amber)
    - NEGLECTED (red)
    - NEW (slate/blue)
    - STREAK (purple)

## Data Model
Habit object:
- id: string
- name: string
- created: ISO string
- completions: string[] (YYYY-MM-DD)

Storage:
- localStorage key versioned (e.g., habit-tracker-v1)
- Export JSON downloads full state

## Core Features (v1)
### Habits
- Add habit (name required)
- Track completion by date (checkbox grid)
- Rename habit (v1.1 target)
- Delete habit (v1.1 target)

### Views
- Weekly view (default): Mon–Sun
- Monthly view: days 1–31; show “—” for non-existent days
- Toggle weekly/monthly from top controls

## Analytics (v1)
Per habit:
- Week completion: X/7 and %
- Month completion: X/daysInMonth and %
- Current streak (consecutive days ending today)
- Days since last completion

Insights section content:
- Ring / circle charts (SVG rings, solid stroke color)
- Ranked “Neglected” list (highest days since last)
- Ranked “Top habits” list (highest completion)
- Badges for status (solid colors)

## Coach (Real-time)
### Coach v1 (heuristics, local)
- Updates on every check/uncheck
- Produces:
  - One headline (“what matters most today”)
  - 3–5 bullets (actions)
  - Flags neglected habits
  - Suggests “today priorities”
  - Suggests “shrink the habit” when missed >2 days

### Coach v2 (true AI)
- Single AI provider behind a backend endpoint (no keys in frontend)
- Input: current habits + completion history + derived stats
- Output: short, actionable advice (no fluff), max ~8 lines
- Privacy: do not send anything unnecessary

## Accessibility
- High contrast text
- Keyboard-friendly controls
- Buttons have labels / aria-labels where needed

## Definition of Done (v1)
- Add habit, check/uncheck, persists reliably
- Weekly + Monthly toggle works
- Insights update instantly
- Scroll-in-place sections + expand-to-full behavior works
- Solid-color palette only (no gradients)
- Runs on GitHub Pages with static hosting
