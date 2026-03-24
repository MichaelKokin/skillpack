# Lopaka — Landing Page Redesign Brief

> Ready to paste into Lovable / Bolt / v0

---

## Project

Landing page for Lopaka — a UI graphics editor for embedded screens (Arduino, STM32, ESP32) with pixel-perfect code builder and export. The page must convert visiting hardware developers into registered users who create their first project. The audience is embedded engineers and hobbyists who currently hand-code pixel UIs or use clunky desktop tools — they need to feel that Lopaka is a serious, modern tool that saves hours of pain.

## Stack

React + Tailwind CSS + Framer Motion (animations) + Lucide icons

## Design Tokens

```
Background:       #09090B
Surface:          #141418
Elevated surface: #1C1C22
Primary text:     #F4F4F5
Muted text:       #71717A
Accent:           #F97316   (orange — inherited from Lopaka's brand)
Accent hover:     #FB923C
Success:          #22C55E   (for "code exported" states)
Border:           #27272A
Code background:  #0C0C0F
```

Dark theme is mandatory — embedded developers live in dark IDEs. Orange accent connects to Lopaka's existing brand color (#ff8200), refined to feel more modern.

## Typography

```
Display:      Inter, 56px, -0.025em tracking, font-weight 800
Headline:     Inter, 32px, -0.015em tracking, font-weight 700
Subheadline:  Inter, 20px, -0.01em tracking, font-weight 500
Body:         Inter, 16px, normal tracking, font-weight 400
Code/mono:    JetBrains Mono, 14px, normal tracking, font-weight 400
Caption:      Inter, 13px, 0.01em tracking, font-weight 500
```

Two typefaces: Inter for everything human-readable, JetBrains Mono for code snippets and technical specs. Both free, both loved by developers.

## Composition Rules

- The first viewport reads as ONE complete idea: "design embedded UIs visually, export pixel-perfect code"
- Brand name "Lopaka" is hero-level — large, bold, unmistakable
- Full-bleed hero with edge-to-edge dark background and a glowing product screenshot
- Hero budget: logo + headline + one sentence + CTA ("Start Building — Free") + product visual. Nothing else.
- No floating badges, decorative overlays, or "trusted by 10,000 devs" counters on the hero
- No cards by default. Use cards ONLY for the platform comparison (Adafruit GFX vs u8g2 vs TFT_eSPI)
- Each section has exactly ONE job and ONE headline
- Every image shows the actual product — editor screenshots, real code output, real embedded screen renders
- No generic stock photos of circuit boards or "developer at laptop"
- No pill clusters, icon grids, or "feature bento boxes"
- No filler copy. Every sentence addresses a specific pain or shows a specific capability.
- One accent color (orange). Green only for success states in code examples.

## Page Structure

### Section 1 — Hero
Full-bleed dark background. Large product screenshot showing the editor with a real UI layout on an OLED screen preview.

**Headline:** "Design embedded UIs visually. Export pixel-perfect code."

**Supporting line:** "The graphics editor for Arduino, ESP32, and STM32 that replaces hand-coding every pixel. Draw your UI, get production-ready C code."

**CTA:** "Start Building — Free" (primary, orange) + "See How It Works" (secondary, ghost button)

The product screenshot should glow subtly — a faint orange radial gradient behind it to make it pop against the dark background.

### Section 2 — Pain / Problem
**Headline:** "Stop hand-coding pixel coordinates"

Show a before/after: left side is ugly, manual C code with hardcoded pixel values. Right side is the same UI built in Lopaka's visual editor — clean, visual, instant. Use real code snippets in JetBrains Mono.

This section should make every embedded developer feel seen. They've all been there — counting pixels, guessing coordinates, re-uploading to check if the layout is right.

### Section 3 — How It Works (3 steps)
**Headline:** "From idea to code in three steps"

Three horizontal blocks (NOT cards, just clean layout sections):
1. **Draw** — "Use the visual editor to place text, shapes, and images on your target screen size" + editor screenshot
2. **Preview** — "See exactly how it looks on a real display — pixel for pixel" + preview screenshot
3. **Export** — "Get ready-to-compile code for your platform. Copy, paste, upload." + code output screenshot

Each step has a number (large, muted, decorative), a short headline, one sentence, and a product screenshot.

### Section 4 — Platform Support
**Headline:** "Works with your stack"

A clean horizontal row of supported platforms with logos/icons:
- Adafruit GFX
- u8g2
- TFT_eSPI
- Arduino
- ESP32
- STM32

Below that — three small cards (this is where cards are justified) showing platform-specific export examples. Real code, JetBrains Mono, syntax-highlighted.

### Section 5 — Key Features
**Headline:** "Built for embedded, not compromised"

NOT a feature grid. Instead, 3-4 features presented as full-width alternating rows (image left / text right, then flip):

- **Pixel-perfect rendering** — What you see is exactly what gets displayed. No antialiasing surprises, no sub-pixel rendering.
- **Image converter** — Drop in a PNG, get uint8/uint32 arrays ready for your display driver.
- **Custom fonts** — Import any font, see it rendered at your target resolution. No more guessing how FreeMonoBold looks at 8px.
- **Multiple screens** — Design multi-screen UIs with navigation flows. Export everything at once.

Each feature gets ONE sentence explaining what it does and ONE sentence explaining why it matters (the pain it solves).

### Section 6 — Social Proof (if available)
**Headline:** "Trusted by embedded developers"

If there are GitHub stars, user count, or community testimonials — show them here. Keep it tight: one metric or 2-3 short quotes max. If no social proof exists yet, skip this section entirely. Do not fake it.

### Section 7 — Final CTA
**Headline:** "Your next embedded UI starts here"

**Supporting line:** "Free to use. No credit card. Start with a blank canvas and ship real code."

**CTA:** "Create Your First Project" (large, orange, centered)

Dark background, generous whitespace, the CTA button is the only bright element on screen.

### Footer
Minimal. Logo + links: GitHub, Documentation, Terms, Privacy. No multi-column mega-footer.

## Motion

Exactly 3 intentional animations:

1. **Hero entrance** — Product screenshot fades up and scales from 0.95 to 1.0 with a subtle orange glow bloom. Headline fades in 200ms before. Use Framer Motion `initial={{ opacity: 0, y: 30 }} animate={{ opacity: 1, y: 0 }}`.

2. **Before/After code reveal** — In the "Pain" section, the manual code fades out and transforms into the Lopaka-generated code. A satisfying visual metaphor for the product's value.

3. **Scroll-triggered section reveals** — Each section fades in gently as it enters the viewport. Stagger child elements by 100ms. Subtle, not flashy.

No decorative particles, floating elements, or background animations. The product screenshots are the visual anchor — don't compete with them.

## Responsive Behavior

- Mobile-first: design for 375px, then scale up
- Hero screenshot stacks below the headline on mobile
- "How It Works" steps stack vertically on mobile
- Platform row wraps to 2x3 grid on mobile
- Code snippets horizontally scroll on mobile rather than shrinking font
- Touch targets minimum 44x44px on all CTAs
- Navigation collapses to hamburger with: Platforms, Pricing (if exists), Docs, Sign In

## Copy Voice

- Technical but approachable — like Vercel's or Raycast's copywriting
- No buzzwords: no "revolutionary", "game-changing", "unleash", "empower"
- Speak to the developer directly: "your display", "your code", "your stack"
- Every headline is a statement or action, never a question
- Feature descriptions lead with what it DOES, then why it MATTERS

## Do NOT generate:

- Generic SaaS card grids as the first impression
- Hero with circuit board stock photography
- "Trusted by" counters with fake/inflated numbers
- Feature bento box grids with icons
- Gradients that fight with code snippet readability
- Carousel of features — every feature is visible without interaction
- Split-screen hero where neither side has enough room
- More than 2 typefaces
- Glassmorphism or frosted glass effects
- Decorative 3D renders of microcontrollers
- "Join 10,000+ developers" if the number isn't real
- Light theme — this is a developer tool, dark mode only
- Pricing section unless specifically requested
- Any copy that says "Unleash", "Transform", "Supercharge", or "Next-generation"
