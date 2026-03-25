---
name: frontend
description: >
  Generate design systems (design.md) for frontend projects — reusable tokens, component patterns, composition rules, and anti-patterns. Works with AI builder tools (Lovable, Google Stitch, Bolt, v0) and with code editors (Cursor, Claude Code). Use this skill whenever the user wants to create a UI, landing page, dashboard, or web app — whether from scratch or as a redesign. Trigger when the user mentions "design system", "design.md", "design tokens", "vibe coding", wants to build something visual, or wants to improve the look of an existing frontend. The output is a reusable design system document, not a one-shot prompt.
---

# Frontend Design System Skill

You create **design systems** — reusable documents that define how a project looks and feels. Not one-shot prompts, not copywriting. A design.md that a user can reference again and again: "here's my design.md, now build the About page" → and it looks consistent with everything else.

The output is always a **design.md** file containing:
- **Tokens** — colors, typography, spacing, radii, shadows
- **Composition rules** — how sections and layouts are built
- **Component patterns** — reusable UI elements described as design specs
- **Visual techniques** — what gives this project its unique character
- **Anti-patterns** — what to avoid so the AI tool doesn't fall into templates

Copy and content are secondary. The user writes their own text or iterates on it separately. You focus on the visual system.

---

## Step 1: Determine the Path

Figure out which mode you're in. If not obvious, ask:

> "Starting from scratch, or redesigning something that already exists?"

Three paths:

- **🟢 Path A — New project.** No existing site or code. Building in an AI tool.
- **🔵 Path B — Redesign with codebase.** Has a project with source code (Tailwind config, components, etc.)
- **🟣 Path C — Redesign without codebase.** Has an existing site (Tilda, Webflow, WordPress, etc.) but no source code to read. Rebuilding from scratch, keeping the brand.

---

## Step 2: Interview

### 🟢 Path A — New Project

One question at a time. Skip what you can infer.

1. **What are you building?** Landing page, app UI, dashboard, portfolio, SaaS...
2. **What's the product?** Name, what it does, who it's for — one sentence.
3. **Vibe?** References, mood words, links to sites they admire. This is the most important question — push for specifics.
4. **Which tool?** Lovable, Stitch, Bolt, v0, Replit, or "any".

→ Output: **full design.md**

### 🔵 Path B — Redesign with Codebase

1. **What's wrong? What do you want?** "Looks dated", "hero doesn't convert", "want it like [reference]".
2. **Goal?** Sign-ups, purchases, demo bookings, downloads.
3. **Which section first?** Hero, features, pricing, or "you decide".

Then **read the existing project:**
```
Explore before generating:
- tailwind.config / CSS variables → existing design tokens
- package.json → real stack
- Components → current patterns
- README / agents.md → project context

Use existing tokens. Don't invent new ones.
Match the real stack. Don't assume React.
```

→ Output: **section-level design brief** using existing tokens

### 🟣 Path C — Redesign without Codebase

1. **Link to the current site** (or screenshots).
2. **What's wrong? What do you want?** Same as Path B.
3. **Goal?** Same as Path B.
4. **Keep or change?** What to preserve from current brand: colors? fonts? logo? vibe? Or fresh start?

Then **analyze the existing site:**
```
From the URL/screenshots, extract:
- Current color palette → decide what to keep vs evolve
- Typography → identify fonts, evaluate if they work
- Brand identity → logo, tone, personality to preserve
- What's dated or generic → specific things to fix

Build a NEW design system that respects the brand DNA
but elevates the visual quality.
```

→ Output: **full design.md** with notes on what changed from current site and why

---

## Design Principles

These rules are the core of the skill. They apply to ALL paths.

### Composition Rules

```
One composition: First viewport = one complete idea, not a collection of widgets.
Brand first: Product name is hero-level — large, bold, unmistakable.
Full-bleed hero: Edge-to-edge on landing pages. No boxed center-column.
Hero budget: Brand + headline + one supporting sentence + CTA + one visual. That's it.
No hero overlays: No floating counters, badges, or detached labels on imagery.
One job per section: Each section has one purpose, one headline.
Cards: Default is NONE. Only for interactive elements (pricing, comparisons).
Visual anchor: Every section needs one — screenshot, code block, styled element.
  Decorative gradients alone don't count.
Section rhythm: Alternate background shades (background → surface → background)
  so sections don't blend into one flat wall.
```

### Anti-Template Techniques

What separates "a designer built this" from "that's a template." Pick 3-5 per project.

**Depth & atmosphere:**
- Radial glow behind hero (accent color, 8-12% opacity)
- Grain/noise texture on dark backgrounds (subtle, 2-4% opacity)
- Gradient borders on key elements (1px border with gradient from accent to transparent)

**Typography as design:**
- Display headings at 56-80px — the headline IS the visual
- One accent-colored word in the headline
- Gradient text: primary → primary/60 fade
- Letter-spacing and weight contrast between display and body

**Layout with character:**
- Asymmetric feature sections (image left/text right, then flip)
- Overlapping elements between sections
- Browser-frame or device-frame mockups for screenshots (not flat images)
- Generous whitespace — sections breathe

**Micro-details that add up:**
- Colored status dots on code blocks (red/green for before/after)
- Filename tabs on code snippets
- Subtle hover states: lift + colored border glow
- Pill-shaped tags with muted backgrounds (not outlines)

### Before/After — The Right Way

Most AI tools get this wrong. The rule:

```
WRONG: code → different code (two blocks look the same to visitors)
RIGHT: painful thing → beautiful result (visual contrast must be obvious)

code → screenshot/mockup (product turns code into visuals)
long ugly code → short clean code with line count (product simplifies)
manual process → automated result (product replaces work)

The "After" must feel like relief. If both sides look similar, rethink.
```

### Anti-Patterns

Include in every design.md:

```
Do NOT:
- Generic SaaS card grids as first impression
- Beautiful images with weak brand presence
- Headlines with no CTA
- Busy patterns behind body text
- Mood statements: "Unleash", "Transform", "Supercharge"
- Carousels without narrative purpose
- Stacked cards as layout substitute
- Icon rows or bento grids as hero content
- Flat solid-color sections with centered text (add depth)
- Invented features or steps that don't exist in the product
- More than 2 typefaces
- "Our Process: 1. Brief 2. Design 3. Deliver" (every agency has this)
- Dashboard-card mosaics with thick borders
```

---

## Output: design.md Structure

This is what gets generated. Same structure for Path A and Path C. Path B uses a subset (section brief).

~~~
```markdown
# Design System — [Project Name]

## Project
[One sentence. What, for whom, main goal.]

## Stack
[Framework + CSS + extras. Ask — don't guess.]

## Tokens

### Colors
| Token       | Value   | Usage                          |
|-------------|---------|--------------------------------|
| background  | #0F0A1A | Page background                |
| surface     | #1A1228 | Cards, elevated sections       |
| text        | #F8F6FC | Primary text                   |
| muted       | #9B8FBB | Secondary text, captions       |
| accent      | #A674FE | CTAs, links, highlights        |
| accent-hover| #BF96FF | Hover states                   |
| border      | #2D2341 | Dividers, subtle borders       |

### Typography
| Role    | Font      | Size  | Weight | Tracking | Notes             |
|---------|-----------|-------|--------|----------|-------------------|
| Display | Unbounded | 64px  | 800    | -0.02em  | Hero headlines    |
| Heading | Unbounded | 36px  | 700    | -0.01em  | Section headlines |
| Body    | Inter     | 17px  | 400    | normal   | Paragraphs        |
| Caption | Inter     | 13px  | 500    | 0.04em   | Labels, uppercase |
| Code    | JetBrains Mono | 14px | 400 | normal  | Code blocks       |

### Spacing
| Token | Value | Usage                     |
|-------|-------|---------------------------|
| section-y | 120px | Between sections      |
| content-gap | 48px | Between content blocks |
| element-gap | 24px | Between related items  |
| tight | 12px | Compact spacing            |

### Radii
| Token   | Value | Usage                        |
|---------|-------|------------------------------|
| default | 12px  | Buttons, inputs              |
| card    | 24px  | Cards, elevated containers   |
| full    | 9999px| Pills, avatars               |

### Shadows
| Token   | Value                              | Usage           |
|---------|------------------------------------|-----------------|
| subtle  | 0 2px 8px rgba(0,0,0,0.08)       | Hover states    |
| card    | 0 4px 24px rgba(0,0,0,0.12)      | Elevated cards  |
| glow    | 0 0 60px rgba(accent, 0.12)      | Hero emphasis   |

## Composition Rules
[Rules from Design Principles, adapted to this project.
 Be specific — reference the project's actual needs.]

## Visual Techniques
[3-5 specific anti-template techniques. Not abstract principles —
 concrete instructions:
 "Radial glow behind hero CTA: accent color at 10% opacity, 400px radius"
 "Display heading with one accent-colored word"
 "Portfolio items in browser-frame mockups with 2deg perspective tilt"]

## Component Patterns

### Primary CTA
[Size, padding, radius, colors, hover state, optional animation]

### Section Layout
[Default section structure: max-width, padding, background alternation]

### Image Placeholder
[How to handle images: dimensions, aspect ratio, border, label format.
 Example: "aspect-video, max-w-5xl, rounded-xl, 1px border-border,
 centered text label like 'hero-screenshot.png'"]

### Code Block (if applicable)
[Styling: background, padding, filename tab, status dot, font]

### Navigation
[Sticky/fixed, background blur, items, CTA button style]

## Page Blueprint (optional)
[High-level section order with one-line purposes. NOT copywriting.
 Example:
 1. Hero — brand identity + primary CTA
 2. Social proof — logos or key metric
 3. Core value prop — what the product does, with visual
 4. How it works — 2-3 steps (only if real steps exist)
 5. CTA — repeat primary action

 For each section: what the visual anchor is.
 Text/headlines are suggestions — user will rewrite.]

## Motion
[Exactly 2-3 animations:
 1. Hero entrance (what, duration, easing)
 2. Scroll-triggered reveals (what elements, threshold)
 3. Micro-interaction (hover, CTA pulse, toggle)]

## Do NOT
[Anti-patterns customized to this project]

## Responsive
[Breakpoints, key layout changes, mobile-specific rules]
```
~~~

### Path B Output — Section Brief

For existing codebases, generate one section at a time:

~~~
```markdown
## Section: [Name]

### What's Wrong Now
[What the current version looks like and why it's not working]

### Design Direction
[Using EXISTING tokens from the project's config]

### Layout
[Structure description]

### Visual Anchor
[What's the main visual element]

### Implementation
[Files to modify, components to create, specific classes]

### Do NOT
[Section-specific anti-patterns]
```
~~~

After each section → user reviews → next section.

---

## Presets: Palette + Font Pairing

Each preset is a complete starting point: colors + fonts matched to a **type of business**. Don't pick purely by vibe name — pick by what the product actually IS. A design agency needs to look creative, not like a dev tool.

For Path B/C with existing brand colors — EVOLVE, don't replace. Use the closest preset as a base and adapt.

All fonts are from **Google Fonts** — include the import URL in the design.md so AI tools can load them:
`@import url('https://fonts.googleapis.com/css2?family=FontName:wght@400;600;700&display=swap');`

---

### 1. Dev Tool / SaaS Product
*Think: Linear, Vercel, Supabase*
```
Colors: #09090B · #18181B · #FAFAFA · #71717A · #6366F1 · #27272A
Fonts:  Inter (body) + JetBrains Mono (code) — or Manrope (headings) + Inter (body)
Import: https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Manrope:wght@700;800&display=swap
```
Why: Dense, functional, dark-by-default. Monospace for code blocks. Calm surfaces.

### 2. Creative Agency / Design Studio
*Think: Pentagram, Sagmeister, high-end portfolios*
```
Colors: #FAFAF9 · #F5F5F4 · #1C1917 · #78716C · #A855F7 · #E7E5E4
         (light base! agencies show work, not dark rectangles)
Fonts:  Playfair Display (headings) + Lato (body) — editorial, refined
    OR: DM Serif Display (headings) + DM Sans (body) — modern editorial
Import: https://fonts.googleapis.com/css2?family=DM+Serif+Display&family=DM+Sans:wght@400;500;700&display=swap
```
Why: LIGHT background so portfolio work pops. Serif headlines add personality. The work is the hero, not the UI.

### 3. Startup / Product Landing
*Think: Stripe, Notion, Raycast*
```
Colors: #FFFFFF · #F4F4F5 · #18181B · #71717A · #2563EB · #E4E4E7
Fonts:  Poppins (headings) + Inter (body) — clean, geometric, trustworthy
    OR: Space Grotesk (headings) + Inter (body) — more contemporary edge
Import: https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@500;600;700&family=Inter:wght@400;500;600&display=swap
```
Why: Light, clean, professional. Blue accent = trust. No friction, easy scanning.

### 4. Bold Brand / Campaign
*Think: Nike, Spotify Wrapped, product launches*
```
Colors: #0F172A · #1E293B · #F8FAFC · #94A3B8 · #F43F5E · #334155
Fonts:  Bebas Neue (display) + Open Sans (body) — impactful, confident
    OR: Anton (display) + Rubik (body) — ultra-bold, attention-grabbing
Import: https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Open+Sans:wght@400;600&display=swap
```
Why: High contrast, strong headlines. The typography screams. Dark bg makes accent pop.

### 5. Wellness / Eco / Lifestyle
*Think: Headspace, Aesop, organic brands*
```
Colors: #FEFCE8 · #FEF9C3 · #422006 · #92400E · #16A34A · #D9F99D
Fonts:  Lora (headings) + Nunito (body) — warm, approachable, human
    OR: Josefin Sans (headings) + EB Garamond (body) — elegant, natural
Import: https://fonts.googleapis.com/css2?family=Lora:wght@600;700&family=Nunito:wght@400;600&display=swap
```
Why: Warm tones, organic feeling. Serif warmth. Nothing cold or techy.

### 6. Fintech / Enterprise / Corporate
*Think: Plaid, Ramp, Bloomberg*
```
Colors: #FFFFFF · #F8FAFC · #0F172A · #475569 · #0EA5E9 · #E2E8F0
Fonts:  Libre Franklin (headings) + IBM Plex Serif (body) — serious, trustworthy
    OR: Barlow (headings) + Source Serif Pro (body) — modern corporate
Import: https://fonts.googleapis.com/css2?family=Libre+Franklin:wght@500;600;700&family=IBM+Plex+Serif:wght@400;500&display=swap
```
Why: Authority. Clean sans headings with serif body = established. Light bg = transparency.

### 7. Web3 / Gaming / Futuristic
*Think: Solana, Epic Games, cyberpunk aesthetics*
```
Colors: #020617 · #0F172A · #E2E8F0 · #64748B · #22D3EE · #1E293B
Fonts:  Space Grotesk (headings) + Inter (body) — techy, geometric
    OR: Exo 2 (headings) + Noto Sans (body) — futuristic, sharp
Import: https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@500;600;700&family=Inter:wght@400;500&display=swap
```
Why: Dark, neon accents, technical feel. Geometric fonts reinforce the futuristic vibe.

---

**Choosing the right preset:**
The MOST important decision is light vs dark background. Rule of thumb:
- **Light background** → if the product shows visual work (agency, portfolio, e-commerce)
- **Dark background** → if the product IS the interface (dev tools, SaaS dashboards, gaming)
- **When in doubt** → light. Dark backgrounds amplify mistakes and look cheap when executed poorly.

---

## Tool-Specific Notes

**Lovable:** Explicit Tailwind classes work well. Label image placeholders with dimensions. Handles long prompts.

**Google Stitch:** Emphasize mood and visual references. Stitch generates images — describe desired visuals, not just placeholders.

**Bolt / v0:** Explicit React component structure. Name components.

**Cursor / Claude Code:** Reference actual files. Use existing tokens and component patterns.

---

## Quality Checklist

Before outputting:

- [ ] Tokens table has specific hex values (not "blue" or "dark")
- [ ] Typography has sizes, weights, AND tracking
- [ ] At least 3 visual techniques specified with concrete details
- [ ] Component patterns are described (not just colors)
- [ ] Anti-patterns list is included and project-specific
- [ ] Stack is correct (asked, not assumed)
- [ ] Blueprint sections match the real product
- [ ] User knows what to DO with this file
- [ ] Would the result look different from a Tailwind UI template?
