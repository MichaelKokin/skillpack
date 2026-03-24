# Design System — Kachkovenko.Design

## Project
Design studio (presentations, web design, courses). Two founders — Max & Anya. Goal: leave a request.

## Stack
React + Tailwind CSS + Framer Motion (for section reveals and hero entrance)

## Tokens

### Colors

Evolved from current brand. Kept signature purple, deepened backgrounds for premium feel.

| Token        | Value   | Usage                          | Notes                          |
|--------------|---------|--------------------------------|--------------------------------|
| background   | #0C0716 | Page background                | Deeper than current #273043    |
| surface      | #16112A | Cards, elevated sections       | Purple-tinted dark             |
| surface-alt  | #1E1638 | Alternating section backgrounds| Prevents flat wall effect      |
| text         | #F4F0FC | Primary text                   | Warm white with purple tint    |
| muted        | #8B7EAD | Secondary text, captions       | Softer than pure gray          |
| accent       | #A674FE | CTAs, links, active states     | KEPT from current brand        |
| accent-hover | #BF96FF | Hover states                   |                                |
| accent-secondary | #7492FE | Secondary actions, tags    | KEPT — the blue from current   |
| border       | #2A2045 | Dividers, card borders         |                                |
| success      | #4ADE80 | Positive states                |                                |
| warning      | #FBBF24 | Alerts                         |                                |

### Typography

| Role    | Font      | Size  | Weight | Tracking | Line-height | Notes                     |
|---------|-----------|-------|--------|----------|-------------|---------------------------|
| Display | Unbounded | 64px  | 800    | -0.02em  | 1.1         | KEPT — brand signature    |
| H1      | Unbounded | 48px  | 700    | -0.015em | 1.15        | Page-level headlines      |
| H2      | Unbounded | 32px  | 700    | -0.01em  | 1.2         | Section headlines         |
| H3      | Unbounded | 22px  | 600    | -0.005em | 1.3         | Subsection headers        |
| Body    | Inter     | 17px  | 400    | normal   | 1.65        | NEW — readability upgrade |
| Body-sm | Inter     | 15px  | 400    | normal   | 1.6         | Compact text              |
| Caption | Inter     | 13px  | 500    | 0.04em   | 1.4         | Labels, uppercase         |
| Button  | Inter     | 15px  | 600    | 0.02em   | 1.0         | CTA text                  |

**Why these fonts:** Unbounded is the brand — bold, geometric, distinctive. Kept for all headlines. Added Inter for body text (current site uses Unbounded everywhere, which hurts readability in paragraphs).

### Spacing

| Token       | Value  | Usage                      |
|-------------|--------|----------------------------|
| section-y   | 140px  | Vertical gap between sections |
| content-gap | 56px   | Between content blocks     |
| element-gap | 28px   | Between related items      |
| tight       | 14px   | Compact spacing            |
| container   | 1200px | Max content width          |
| gutter      | 24px   | Side padding (mobile: 16px)|

### Radii

| Token   | Value   | Usage                      |
|---------|---------|----------------------------|
| default | 12px    | Buttons, inputs            |
| card    | 24px    | KEPT — brand signature     |
| large   | 36px    | Hero elements, feature cards|
| full    | 9999px  | Pills, avatars             |

### Shadows

| Token   | Value                                    | Usage            |
|---------|------------------------------------------|------------------|
| subtle  | 0 2px 12px rgba(166,116,254, 0.06)     | Default elevation|
| card    | 0 8px 32px rgba(166,116,254, 0.10)     | Hovered cards    |
| glow    | 0 0 80px rgba(166,116,254, 0.15)       | Hero accent glow |

Note: shadows use accent color, not black. This keeps the purple warmth consistent.

---

## Composition Rules

```
First viewport = studio identity. Not a generic agency hero.
Personality drives the brand — founders, tone, portfolio. Not stock visuals.
Headline in Unbounded at display size IS the visual — it's bold enough to stand alone.
One primary CTA per viewport. "Оставить заявку" is the one action. Everything else is secondary.
Section rhythm: background → surface-alt → background → surface-alt. Never two identical bg sections in a row.
24px radius is the brand shape language. Use consistently on all containers.
No cards for static info. Cards only for interactive things (service selector, course cards user clicks).
Every section needs a visual anchor: portfolio screenshot, styled element, or video. Not just text on dark bg.
White space is generous. Sections breathe. Don't pack content tight.
```

---

## Visual Techniques

These 5 techniques give the project its character. Apply consistently:

**1. Purple glow atmosphere**
Radial gradient behind hero headline area. Accent color at 12% opacity, ~500px radius. Creates depth without being a "gradient background." CSS: `radial-gradient(circle at 50% 40%, rgba(166,116,254,0.12) 0%, transparent 70%)`

**2. Unbounded as visual weight**
Display headlines at 64px carry sections by themselves. No need for decorative images when the typography is this bold. One word in accent color for emphasis.

**3. Portfolio in device frames**
Project screenshots inside browser-frame or device mockups — not flat images. Frame: surface background, 1px border-border, rounded-card, small top bar with 3 dots. Slight shadow-card on hover.

**4. Asymmetric feature layout**
Feature sections alternate: visual left + text right, then text left + visual right. Not a grid of identical cards. Each feature gets full width to breathe.

**5. Section dividers with gradient borders**
Instead of hard section breaks, use a thin gradient line (accent → transparent) as a subtle section separator. 1px height, 60% width, centered.

---

## Component Patterns

### Primary CTA
```
Background: accent (#A674FE)
Text: white, Button size (15px/600)
Padding: 16px 32px
Radius: default (12px)
Hover: accent-hover (#BF96FF) + shadow-subtle
Active: scale(0.98)
Transition: all 200ms ease
```

### Secondary CTA
```
Background: transparent
Border: 1px solid border (#2A2045)
Text: text (#F4F0FC), Button size
Padding: 16px 32px
Radius: default (12px)
Hover: border-accent + text-accent
```

### Section Container
```
Max-width: container (1200px)
Padding: section-y (140px) vertical, gutter (24px) horizontal
Center aligned
Background alternates: background / surface-alt
```

### Portfolio Card
```
Container: rounded-card (24px), overflow hidden
Image: aspect-video, object-cover
Frame: surface background, 1px border-border
Top bar: 12px height, 3 dots (8px circles in muted color)
Hover: shadow-card + translateY(-4px)
Transition: all 300ms ease
```

### Navigation
```
Position: fixed, top 0, full width
Background: background/80 + backdrop-blur-xl
Padding: 16px gutter
Content: logo left, 3-4 nav items center, CTA button right
CTA in nav: smaller variant of Primary CTA (12px 24px padding)
Z-index: 50
Border-bottom: 1px solid border (appears on scroll)
```

### Image Placeholder
```
Aspect: aspect-video (16:9 default) or aspect-[4/3]
Max-width: max-w-5xl
Background: surface
Border: 1px solid border
Radius: rounded-card (24px)
Label: centered, muted color, Caption size
Format: "section-name.png" (e.g., "hero-screenshot.png")
```

---

## Page Blueprint

Section order with purposes. Texts are sketches — rewrite freely.

1. **Hero** — Studio identity + primary CTA
   - Visual: Unbounded display headline + purple glow. Personality-first.
   - Anchor: typography itself or a single strong portfolio piece

2. **Portfolio** — Best work speaks for itself
   - Visual: 3-4 projects in device frames, asymmetric grid
   - Anchor: real project screenshots (placeholders for now)

3. **Services** — Three directions, user picks their path
   - Visual: three columns with distinct icons/visuals per service
   - NOT cards — simple text blocks with links
   - Presentations / Web Design / Courses

4. **Social proof** — One strong testimonial or client logos
   - Visual: large quote in Unbounded italic + logo row (grayscale → color on hover)
   - One quote beats five weak ones

5. **CTA** — Clear call to action
   - Visual: accent glow background, prominent form or button
   - "Обсудить проект" → form or link to contact

---

## Motion

Three animations total:

1. **Hero entrance:** Headline fades up with 200ms stagger per line. Opacity 0→1 + translateY 30px→0. Duration: 600ms. Easing: cubic-bezier(0.16, 1, 0.3, 1).

2. **Scroll reveals:** Sections fade in when 20% visible. Opacity 0→1 + translateY 40px→0. Duration: 500ms. Stagger children by 100ms. Use Framer Motion `whileInView`.

3. **Portfolio hover:** Card lifts 4px + shadow grows. Duration: 300ms ease. Subtle, not dramatic.

---

## Do NOT

```
- Generic agency hero with stock photos of people in meetings
- Card grid of services as first impression
- "Our Process: 1. Brief 2. Design 3. Deliver" section (every agency has this)
- Carousel of testimonials
- Icon rows (pen icon for design, screen icon for web — boring)
- Split-screen hero
- Gradient backgrounds that fight with text
- Multiple competing CTAs in one viewport
- "Trusted by" logo bar right after hero (earn attention first)
- Decorative blobs or abstract shapes
- Same background color for adjacent sections
- Unbounded for body text (only headlines)
```

---

## Responsive

| Breakpoint | Key changes |
|------------|-------------|
| Desktop (>1200px) | Full layout, 64px display, 2-3 column grids |
| Tablet (768-1200px) | Display → 48px, portfolio → 2 columns, container padding 32px |
| Mobile (<768px) | Display → 36px, single column, portfolio → horizontal scroll, nav → hamburger with fullscreen overlay, section-y → 80px |

Touch targets: minimum 44x44px.
Images: aspect-ratio containers to prevent layout shift.
Nav on mobile: hamburger → fullscreen overlay with large tap targets.

---

## What Changed from Current Site

| Current (Tilda) | design.md | Why |
|---|---|---|
| Unbounded everywhere | Unbounded headlines + Inter body | Body text readability |
| #273043 navy background | #0C0716 deep purple-black | More depth, more premium |
| Two hero CTAs competing | One primary CTA | Focus converts better |
| Bright purple on navy | Same purple on deeper dark | More contrast, less flat |
| Rounded 24px everywhere | 24px for cards, 12px for buttons | Hierarchy of shapes |
| No section rhythm | Alt backgrounds + gradient dividers | Visual breathing room |
