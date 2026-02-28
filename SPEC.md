# Habit Tracker — Project Spec (v1)

## Purpose
Build a minimalist, Stack-style habit tracker with real-time insights and a coach system.

## Non-negotiables
- Minimalist, bold UI
- Solid colors only (no gradients)
- Clean typography
- Top section: habit operations (check-ins)
- Bottom section: insights + coach
- Fast, distraction-free

## Platform
- Static frontend (GitHub Pages)
- Local-first storage (browser)
- No login required (v1)

## Data Model
Habit:
- id: string
- name: string
- created: ISO string
- completions: string[] (YYYY-MM-DD)

## Views
### Weekly
- Monday → Sunday grid
- Checkbox per habit per day

### Monthly
- Calendar grid
- Completion % per habit

## Analytics
- Completion rate (week + month)
- Current streak
- Days since last completion
- Neglected habits list

## Coach (v1 – heuristic)
- Real-time analysis of behavior
- Flags neglected habits
- Suggests today’s priorities
- Encourages streak protection

## Coach (v2 – AI)
- Single backend AI endpoint
- Summarizes habits + trends
- Gives short, actionable advice
- No API keys in frontend

## Definition of Done (v1)
- Add / track habits
- Data persists reliably
- Insights update instantly
- Clean UI, no clutter
- Runs on GitHub Pages
