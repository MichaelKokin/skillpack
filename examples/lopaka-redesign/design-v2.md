# Lopaka — Landing Page Redesign Brief v2

> Ready to paste into Lovable

## Project

Landing page for Lopaka — a visual UI editor for embedded screens (Arduino, STM32, ESP32) that exports pixel-perfect C code. Target audience: embedded developers and hobbyists who are tired of hand-coding pixel coordinates. Goal: get the visitor to sign up and create their first project.

## Stack

React + Tailwind CSS + Framer Motion + Lucide icons + JetBrains Mono (for code)

## Design Tokens

```
--background:     #08080A
--surface:        #121215
--elevated:       #1A1A1F
--text:           #F4F4F5
--muted:          #71717A
--accent:         #F97316
--accent-hover:   #FB923C
--success:        #22C55E
--border:         #1F1F23
```

Dark theme only. Orange accent `#F97316` is the brand color. Use it sparingly — CTAs, one word in headlines, active states. Everything else is neutral.

## Typography

```
Display:   Inter, 72px, -0.03em, font-weight 800, line-height 1.0
Headline:  Inter, 36px, -0.02em, font-weight 700
Body:      Inter, 17px, normal, font-weight 400, line-height 1.6
Code:      JetBrains Mono, 14px, normal, font-weight 400
Caption:   Inter, 13px, 0.01em, font-weight 500, text-transform uppercase, color muted
```

Two typefaces only. Inter for all UI, JetBrains Mono for code. Display size is intentionally large — the headline IS the visual anchor of the hero.

## Hard Rules

```
One composition: The first viewport reads as one complete idea, not a collection of widgets.
Brand first: "Lopaka" is hero-level — 13px uppercase caption above the main headline, colored in accent.
Typography as hero: The 72px headline IS the visual — no need for a massive illustration.
Background: Subtle radial gradient glow (accent, 10% opacity) behind hero content. Not flat black.
Full-bleed: Edge-to-edge dark background. No boxed center-column layout.
Hero budget: Brand label + headline + one sentence + two CTAs + one product image below. That's it.
No hero overlays: No floating badges or stat counters on the hero.
Cards: NO cards anywhere except platform-specific code export examples.
One job per section: Each section has one purpose and one headline.
Real visual anchor: Product screenshot placeholders where noted. Code blocks as visual elements elsewhere.
Reduce clutter: No pill clusters, icon rows, stat strips, or feature grids.
Motion: 3 intentional motions (see Motion section). No decorative particles or background animation.
```

## Visual Strategy

```
Hero background: Radial gradient glow centered behind the headline.
  CSS: bg-[radial-gradient(ellipse_at_top,_rgba(249,115,22,0.08)_0%,_transparent_60%)]

Product visuals: Use image placeholder containers (rounded-xl, border border-border,
  bg-surface, aspect-video) with a centered label like "lopaka-editor-hero.png".
  The user will replace these with real screenshots.

Code blocks: Style as design elements — dark elevated background, accent-colored
  syntax highlighting, filename tab header, rounded corners. Use REAL Adafruit_GFX
  code examples from the product, not generic placeholder code.

Section depth: Alternate between --background and --surface for section backgrounds.
  No section should be flat --background with just centered text.

Accent glow: CTA buttons have a subtle box-shadow glow:
  shadow-[0_0_30px_rgba(249,115,22,0.25)] on hover.
```

## Page Structure

### 1. Hero
Full-bleed dark background with subtle accent radial glow at top.

```
[LOPAKA]                                    ← 13px uppercase, accent color

Design embedded UIs visually.               ← 72px display, white
Export pixel-perfect code.                   ← 72px display, accent color

The graphics editor for Arduino, ESP32,     ← 17px body, muted
and STM32. Draw your interface, get
production-ready C code.

[Start Building — Free →]  [See How It Works]  ← primary orange + ghost button
```

Below the CTAs: one large product screenshot placeholder (aspect-video, max-w-5xl, centered). Label it `lopaka-editor-hero.png`. Give it a subtle accent glow shadow and rounded-xl border.

### 2. Pain → Solution (Before / After)
**Headline:** "Stop hand-coding pixel coordinates"
**Subline:** One sentence about the pain every embedded dev knows.

Two-column layout:
- **Left: "Before"** — A real code block showing manual `display.setCursor(12, 8)` calls. 12-15 lines of painful Adafruit_GFX code. Dark elevated background, red-tinted syntax (to feel like "bad" code). Filename tab: `main.cpp — manual approach`
- **Right: "After — with Lopaka"** — Same UI built visually. Either a product screenshot placeholder OR a cleaner, shorter code output with green-tinted syntax. Filename tab: `main.cpp — exported from Lopaka`

This section should feel like a visual "aha" — the contrast between pain and solution.

### 3. How It Works (3 steps)
**Headline:** "From idea to code in three steps"

Horizontal layout, three columns. Each step:
- Large muted number (01, 02, 03) as decorative element
- Bold step name + Lucide icon
- One sentence description
- Product screenshot placeholder below (aspect-video, labeled)

```
01 Draw          02 Preview         03 Export
[pencil icon]    [monitor icon]     [download icon]
Place text,      See pixel-perfect  Get ready-to-compile
shapes, images   render on target   code for your platform.
on your screen.  display size.      Copy, paste, upload.

[placeholder]    [placeholder]      [placeholder]
```

Background: --surface (to contrast with --background hero above).

### 4. Platform Support
**Headline:** "Works with your stack"

A clean horizontal row of platform names in monospace font (not logos, not icons — just styled text):
`Adafruit GFX` · `u8g2` · `TFT_eSPI` · `Arduino` · `ESP32` · `STM32`

Below: three side-by-side code blocks showing the exact same UI exported for three different platforms. Each code block has a filename tab header (`adafruit_gfx.h`, `u8g2.h`, `tft_espi.h`). Real syntax-highlighted code. These ARE the visual anchors — no images needed.

Background: --background.

### 5. Final CTA
**Headline:** "Your next embedded UI starts here"
**Subline:** "Free to use. No credit card. Start with a blank canvas."

One large centered CTA button: "Create Your First Project →"
Accent background, glow shadow on hover. Generous whitespace above and below.

Background: --surface with subtle radial glow behind the button.

### Footer
Minimal single row: Lopaka logo (text) · GitHub · Docs · Terms · Privacy.
Muted text, --background. No multi-column mega-footer.

## Motion

```
1. Hero entrance: Headline fades up (y: 20→0, opacity: 0→1, 600ms ease-out).
   Product screenshot fades in 300ms later with subtle scale (0.97→1).
   Use Framer Motion.

2. Before/After reveal: When section enters viewport, "Before" code block
   appears first, then "After" slides in from the right after 400ms delay.
   Stagger effect that tells a story.

3. CTA glow pulse: Final CTA button has a slow, subtle glow pulse animation
   (box-shadow oscillates between 0.15 and 0.3 opacity over 3s, infinite).
   Draws the eye without being aggressive.
```

No scroll-hijacking, no parallax, no decorative floating elements.

## Do NOT generate:

```
- Card grids as first impression
- Icon rows or feature bento boxes
- Stock photos of circuit boards or "developer at laptop"
- Floating stat counters ("10,000+ users") unless the numbers are real
- Mood copy: "Unleash", "Transform", "Supercharge", "Revolutionary"
- Carousels of any kind
- Glassmorphism or frosted glass panels
- Light theme — dark mode only
- Dashboard-style mosaics or thick-bordered regions
- More than one accent color (orange only, green only for code success states)
- Placeholder lorem ipsum text — all copy must be real
- Decorative background animations or particles
```

## Responsive

```
- Mobile-first: 375px base, scale up
- Hero headline drops to 40px on mobile
- Before/After stacks vertically on mobile
- 3-step section stacks vertically with numbers as left-aligned decorative elements
- Platform code blocks: horizontal scroll on mobile, don't shrink font
- Touch targets minimum 44x44px
- Single-column layout below 768px
```
