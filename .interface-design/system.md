# Design System — saadmkhan.com

## Direction
Sophistication & Trust + Editorial/Magazine
Cool blues, deep navy, structured layout, Plus Jakarta Sans display, Manrope body.
PDLC pages push this further: large typographic ghost stage numbers, vertical timeline, scroll reveals.

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
- Display Font: Plus Jakarta Sans (weights 400,500,600,700,800)
- Body Font: Manrope (weights 400,500,600,700)
- h1: clamp(3rem,6vw,5rem), weight 800, letter-spacing -0.03em
- h2: 1.25rem, weight 700, letter-spacing -0.01em
- Body: 15px, weight 400, line-height 1.7
- Label: 11px, weight 700, letter-spacing .08em, uppercase

## Spacing Scale (4px grid)
4, 8, 12, 16, 20, 24, 32, 40, 48, 64, 80, 96

## Border Radius
- Pill:   99px (badges, stage chips)
- Small:  8px  (metric cards)
- Medium: 12px (cards)
- Large:  16px (section cards, rounded-2xl)

## Shadow System
- Nav:   0 20px 40px rgba(0,93,163,0.06)
- Card:  box-shadow: shadow-sm (Tailwind)
- CTA hover: 0 8px 28px rgba(0,93,163,0.28)
- Stage dot: 0 0 0 4px rgba(0,93,163,0.12)

## PDLC Component Patterns

### Ghost Stage Number
- Font: Plus Jakarta Sans 800, 7rem, opacity 0.055
- Color: #005da3
- Position: absolute right:-8px top:-20px
- pointer-events:none; user-select:none

### Vertical Timeline
- tline: 2px wide, rgba(171,173,175,0.22), left:31px
- tline-fill: animated fill driven by scroll position
- Stage dot: 22px circle, left:21px, done=filled primary

### Stage Section
- padding-left: 56px (pl-14)
- border-left: 3px solid #005da3 on completed stages
- Cards: bg-surface-container-lowest, rounded-2xl, shadow-sm

### PDLC Teaser Card (case study injection point)
- Placed before </main>, after nav links
- background: linear-gradient(135deg,#eef1f3,#e8f0fb)
- border: border-primary/20
- Contains: label badge, h3, tagline, 6-node strip, CTA button

### Sticky Progress Bar
- position:sticky top:0 z-40
- background: rgba(255,255,255,0.92) + backdrop-filter blur(20px)
- Strip nodes: 38px circles, done=primary filled

### Artifact Chip
- inline-flex, gap:5px, padding:4px 11px
- border-radius:99px, bg:#eef1f3, border:rgba(171,173,175,0.3)
- font:11px 600, color:#595c5e

## Scroll Reveal Animation
- Class .reveal: opacity 0, translateY(28px)
- Class .reveal.visible: opacity 1, translateY(0)
- transition: 0.65s ease
- Triggered via IntersectionObserver (threshold 0.1)
- Stagger: 80ms per stage (transition-delay)

## Anti-Patterns
- No generic purple gradients
- No system fonts (no -apple-system, Arial, sans-serif without Plus Jakarta/Manrope)
- No stage descriptions over 3 sentences in deep dive pages
- No inline JS event listeners — use named functions
- PDLC page nav must match case study page nav exactly
- Never use pure #000000 for text — use #2c2f31 (on-surface)

## Files
- chrome-notifications-pdlc.html — Chrome PDLC deep dive (256 lines)
- ai-email-assistant-pdlc.html  — AI Email PDLC deep dive (256 lines)
- chrome-notifications.html     — Teaser card injected at bottom
- ai-email-assistant.html       — Teaser card injected at bottom
