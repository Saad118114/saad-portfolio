# Design System — saadmkhan.com
Last updated: April 2026 (post PDLC merge)

## Direction
Sophistication & Trust + Editorial/Magazine
Cool blues, deep navy, structured layout, Plus Jakarta Sans display, Manrope body.

## Color Tokens
- Background:      #f5f7f9
- Surface:         #ffffff
- Surface Low:     #eef1f3
- Border:          rgba(171,173,175,0.2)
- Text Primary:    #2c2f31
- Text Secondary:  #595c5e
- Accent:          #005da3
- Accent Light:    #4ea4ff
- Accent Container:#e8f0fb
- Stage Complete:  #005da3
- Stage Active:    #4ea4ff (with pulse animation)
- Stage Todo:      #abadaf

## Typography
- Display Font: Plus Jakarta Sans (400,500,600,700,800)
- Body Font: Manrope (400,500,600,700)
- h1: clamp(3rem,6vw,5rem), weight 800, letter-spacing -0.03em
- h2: 1.5–2rem, weight 700–800, letter-spacing -0.02em
- h3: 1.125rem, weight 700, font-family Plus Jakarta Sans
- Body: 14–15px, weight 400, line-height 1.7
- Label: 11px, weight 700, letter-spacing .08em, uppercase

## Spacing Scale (4px grid)
4, 8, 12, 16, 20, 24, 32, 40, 48, 64, 80, 96

## Border Radius
- Pill:   99px (badges, stage chips)
- Small:  8px  (metric cards = 12px)
- Large:  16px (section cards, rounded-2xl)

## Shadow System
- Nav:        0 20px 40px rgba(0,93,163,0.06)
- Card:       shadow-sm (Tailwind)
- CTA hover:  0 8px 28px rgba(0,93,163,0.28)
- Stage dot:  0 0 0 4px rgba(0,93,163,0.12)

## Page Structure (case study pages)
Each case study page is a single merged file containing:
  1. Nav (fixed, back to portfolio)
  2. Hero (title, tag, role date)
  3. Metric grid (real KPIs only — NO role/date cards)
  4. Problem section
  5. Approach section (with interactive demo where applicable)
  6. Outcome section
  7. Nav links (All Case Studies / View LinkedIn)
  8. PDLC Section (Development Journey — full 6 stages inline)
  9. Footer

## PDLC Component Classes (add to <style> block of each case study page)
```
.pdlc-tline   — vertical grey background line (left:31px, 2px wide)
.pdlc-tfill   — animated blue fill line (driven by scroll JS)
.pdlc-ghost   — large ghost stage number (7rem, opacity 0.055, abs right)
.pdlc-stage   — scroll-reveal wrapper (opacity 0 → 1, translateY 28px → 0)
.pdlc-stage.pdlc-vis — visible state triggered by IntersectionObserver
.pdlc-dot     — 22px filled blue circle on timeline (left:21px, absolute)
.pdlc-chip    — artifact pill (11px, eef1f3 bg, border rgba 0.3)
.pdlc-mcard   — metric card (white bg, 12px radius, padding 16/20)
```

## PDLC Section Layout (per stage)
- Container: pl-14 pt-10 pb-2, position:relative
- Dot: .pdlc-dot absolute top:46px
- Ghost number: .pdlc-ghost absolute right:-8px top:-20px
- Card: bg-white rounded-2xl p-7 border border-left:3px solid #005da3
- Stage badge + Complete badge → h3 title → description → artifact chips → 2-col metric cards

## PDLC JS (add before </body> on each case study page)
```js
var pdlcObs = new IntersectionObserver(fn, {threshold:0.1});
document.querySelectorAll('.pdlc-stage').forEach(el => pdlcObs.observe(el));
// updatePdlcLine() on scroll → drives pdlc-fill height based on scroll %
```

## Hero Metric Grid Rules
- ONLY show real product metrics (CTR, users, time saved, scale, revenue)
- NEVER include role dates, tenure, or job title as a metric card
- Chrome: +8pp CTR, +10pp Engagement, 1M+ Users (3-col grid)
- AI Email: 4 hrs saved, 3,000+ users, 50-person pilot, 60x growth (4-col grid)
- EV Advertiser, TellySynco: apply same rule when built

## Case Study Files (current state)
- chrome-notifications.html    — merged, PDLC inline ✅
- ai-email-assistant.html      — merged, PDLC inline ✅
- ev-advertiser.html           — stub, PDLC not yet added
- tellysynco.html              — stub, PDLC not yet added

## Anti-Patterns
- Never put role dates in the metric grid
- Never use system fonts (no -apple-system, Arial, sans-serif without Plus Jakarta/Manrope)
- Never create separate *-pdlc.html pages — PDLC is always embedded in the case study
- No stage descriptions over 3 sentences
- Never use pure #000000 — use #2c2f31 (on-surface)
- PDLC section always uses the gradient card wrapper: linear-gradient(135deg,#eef1f3,#e8f0fb)
