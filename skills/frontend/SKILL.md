---
name: frontend
description: >
  Generate production-quality frontend briefs and prompts for AI builder tools like Lovable, Google Stitch, Bolt, v0, Replit Agent, and similar platforms. Use this skill whenever the user wants to create a UI, landing page, dashboard, web app, or any frontend project using an AI code generation tool. Also trigger when the user mentions "vibe coding", asks to "write a prompt for Lovable/Stitch/Bolt/v0", wants to build something visual, or needs help describing a frontend project to an AI tool. Even if the user just says "make me a landing page" or "I need a dashboard" — this skill helps craft the perfect brief so the AI tool produces polished, professional results instead of generic templates.
---

# Frontend Brief Generator

You help users create detailed, opinionated frontend briefs that produce stunning results when fed into AI builder tools (Lovable, Google Stitch, Bolt, v0, Replit Agent, etc.).

The core insight: AI builder tools produce dramatically better output when given a structured, opinionated brief rather than a vague description. A prompt like "make me a landing page for my SaaS" produces generic garbage. A brief that specifies composition, typography strategy, color tokens, section purposes, and anti-patterns produces something that looks like a real designer built it.

## How This Works

You interview the user, then generate a ready-to-paste prompt. The interview is quick — 4 focused questions, not a 20-question survey. Infer as much as possible from context and fill in smart defaults.

## Interview Flow

### Step 1: Understand the Project

Ask the user ONE message with these questions (skip any you can already infer from context):

1. **What are you building?** (landing page, app UI, dashboard, portfolio, SaaS app, mobile web app, etc.)
2. **What's the product/brand?** (name, what it does, who it's for — even a one-liner is fine)
3. **Any design references or vibes?** (links, screenshots, words like "minimal", "bold", "dark mode", "Linear-style", "Stripe-like")
4. **Which tool are you using?** (Lovable, Stitch, Bolt, v0, or "any" — this affects output format slightly)

If the user already described what they want in their initial message, don't re-ask. Extract what you can and only ask what's missing.

### Step 2: Generate the Brief

Based on their answers, produce a complete brief following the structure below. Wrap it in a code block so they can copy-paste it directly.

---

## Brief Structure

Every brief you generate must include these sections. Adapt the content to the project type (landing page vs app UI vs dashboard), but always maintain this skeleton.

### Section 1: Project Overview & Stack

```
## Project
[One sentence: what this is and who it's for]

## Stack
React + Tailwind CSS + [any extras: Framer Motion for animations, Lucide for icons, etc.]
[If the user specified a different stack, use that instead]
```

### Section 2: Design System

Always define these tokens explicitly. Pick values that match the user's vibe — don't leave them as placeholders.

```
## Design Tokens
- Background: [specific color, e.g., #0A0A0B]
- Surface: [e.g., #141416]
- Primary text: [e.g., #FAFAFA]
- Muted text: [e.g., #71717A]
- Accent: [e.g., #6366F1]
- Accent hover: [e.g., #818CF8]
- Border: [e.g., #27272A]

## Typography
- Display: [e.g., Inter, 64px, -0.02em tracking, font-weight 700]
- Headline: [e.g., Inter, 36px, -0.01em, font-weight 600]
- Body: [e.g., Inter, 16px, normal tracking, font-weight 400]
- Caption/Label: [e.g., Inter, 13px, 0.02em tracking, font-weight 500, uppercase]
- Max two typefaces. [Explain the choice briefly]
```

### Section 3: Hard Composition Rules

These rules are the backbone of the brief. They prevent AI tools from falling into every common trap. Include them in every brief — they're adapted from battle-tested design principles.

```
## Hard Rules

One composition: The first viewport reads as one complete idea, not a dashboard of widgets.
Brand first: Brand/product name is hero-level — large, bold, unmistakable. Not nav text.
Typography: Use expressive, purposeful fonts. No system defaults.
Background: Use gradients, images, or textured surfaces. Not flat solid colors.
Full-bleed hero: Edge-to-edge hero visual. No boxed center-column layout on landing pages.
Hero budget: Brand + headline + one supporting sentence + CTA + one image/visual. That's it.
No hero overlays: No floating badges, stat counters, or detached labels on hero imagery.
Cards: Default is NO cards. Cards only for interactive elements users click through.
One job per section: Each section has exactly one purpose and one headline.
Real visual anchor: Imagery shows product, place, or context. Decorative gradients and abstract shapes alone don't count as a visual anchor.
Reduce clutter: No pill clusters, stat strips, icon rows, or feature grids.
Motion: 2-3 intentional motions that reinforce hierarchy. No decorative animation.
```

### Section 4: Image & Visual Strategy

AI builder tools can't generate real product screenshots — but every section still needs a strong visual anchor. The brief should tell the tool exactly what to render.

```
## Visual Strategy

For product screenshots/images: Use placeholder containers with explicit dimensions,
aspect ratio, a subtle border, and a label like "Product screenshot — editor view".
The user will replace these with real images.

For visual richness WITHOUT images, apply these techniques:
- Accent-colored radial glow behind key elements (hero, CTA)
- Subtle background texture: dot grid, grain, or noise overlay
- Gradient text for hero headline: `bg-gradient-to-r from-white to-white/60 bg-clip-text text-transparent`
- Accent-colored emphasis on one word in headlines
- Syntax-highlighted code blocks as visual elements (using real product code examples)
- Layered surface hierarchy: background → surface → elevated surface
- Alternating section backgrounds for visual rhythm

Every section needs at least one of: real image placeholder, styled code block,
or visual richness technique. No section should be just text on a flat background.
```

This section matters because without it, AI tools produce pages that are structurally correct but visually flat — the "Tailwind UI starter template" problem.

### Section 5: Page Structure

Adapt this based on project type.

**For Landing Pages:**
```
## Page Structure
1. Hero — Brand identity + core promise. Full-bleed visual. One CTA. One product image.
2. Supporting — Show product in context or demonstrate the core pain/solution.
3. Detail — Explain the offering. 2-3 key capabilities max, not a feature dump.
4. Social Proof — Testimonials, logos, or metrics. Only if real. Skip if not.
5. Final CTA — Repeat call to action. Brand + one sentence + button. Clean, spacious.
```

**For App UIs / Dashboards:**
```
## UI Philosophy
Follow Linear-style restraint:
- Calm surface hierarchy (background → surface → elevated surface)
- Strong typography does the heavy lifting, not color
- Dense but readable information layout
- Minimal color usage — accent only for interactive elements and status
- Cards only where interaction demands them (not for static display)
- Sidebar navigation with clean iconography
- Data-first: show the actual content, not chrome around it

## Utility Copy
- Section headings say what the area IS or what users DO there
- Good: "Active Projects", "Search Metrics", "Plan Status"
- Bad: "Unlock Your Potential", "Discover Insights", "Your Journey"
- Prioritize orientation and status over mood and brand voice
```

### Section 6: Motion & Animation

```
## Motion
Ship exactly 2-3 intentional motions:
1. One entrance sequence in the hero (fade-up, scale, or text reveal)
2. One scroll-linked or sticky effect (parallax, reveal-on-scroll, sticky storytelling)
3. One hover/interaction transition (button state, card lift, reveal)

Use Framer Motion for: section reveals, shared layout transitions, scroll-linked effects.
Motions must be noticeable in a quick recording, smooth on mobile, fast and restrained.
No decorative particles, floating shapes, or background animations.
```

### Section 7: Anti-Patterns

Always include this — it's the most impactful section for preventing generic output.

```
## Do NOT generate:
- Generic SaaS card grids as the first impression
- Beautiful images with weak or missing brand presence
- Strong headlines with no clear CTA
- Busy patterns or textures behind body text
- Mood statements that repeat across sections ("Unleash...", "Discover...", "Transform...")
- Carousels without narrative purpose
- Stacked cards as a substitute for real layout design
- Dashboard-card mosaics, thick borders on every region
- Decorative gradients behind routine product UI
- Icon rows or feature bento grids as hero content
- Split-screen hero where the text side is cluttered
- More than 2 typefaces without clear reason
- Flat solid-color sections with just centered text — add visual depth
```

### Section 8: Responsiveness

```
## Responsive Behavior
- Mobile-first: design for 375px, then scale up
- Hero text readable without horizontal scroll on mobile
- Navigation collapses to hamburger or bottom nav
- Touch targets minimum 44x44px
- Images use aspect-ratio containers to prevent layout shift
```

---

## Adapting to the Target Tool

**Lovable**: Loves detailed prompts. Include all sections. Give explicit Tailwind classes where possible (e.g., `bg-zinc-950`, `text-orange-500`). For product images, describe placeholder containers with dimensions — Lovable will render them and the user replaces later.

**Google Stitch**: Visual/design-oriented. Emphasize design tokens, mood, and references. Stitch responds well to style descriptions ("dark, minimal, electric blue accents, generous whitespace").

**Bolt / v0**: React + Tailwind native. Be explicit about component structure (e.g., "Hero component with full-width background, overlay gradient, centered text block").

**Replit Agent**: Prefers step-by-step. Break into phases: "First build the layout skeleton, then styling, then animations."

Default to Lovable format (most detailed) if the user doesn't specify.

---

## Quality Checklist

Before outputting the final brief, verify:
- [ ] Brand/product is unmistakable in the first viewport
- [ ] There's one strong visual anchor per section (image placeholder, code block, or visual technique)
- [ ] Page can be understood by scanning headlines alone
- [ ] Each section has exactly one job
- [ ] Cards are justified (not default)
- [ ] Motion serves hierarchy, not decoration
- [ ] No filler copy or placeholder text in the messaging
- [ ] Color tokens are specific hex values, not "blue" or "dark"
- [ ] Typography specifies sizes, weights, and tracking
- [ ] Anti-patterns section is included
- [ ] Visual strategy addresses what every section looks like — no "just text" sections
- [ ] The brief reads as opinionated design direction, not a generic template

---

## Litmus Test

After generating the brief, mentally ask:
- Is the brand unmistakable in the first screen?
- Is there one strong visual anchor (not a collage)?
- Can the page be understood by scanning headlines only?
- Does each section have one job?
- Are cards actually necessary where used?
- Does motion improve hierarchy or atmosphere?
- Would the page feel premium without decorative chrome?

If any answer is "no" — revise the brief before outputting.

---

## Example Output Format

The final output should be a single code block the user can paste directly:

~~~
```
[FRONTEND BRIEF — ready to paste into Lovable/Stitch/Bolt/v0]

## Project
[description]

## Stack
[stack]

## Design Tokens
[tokens with hex values]

## Typography
[specific fonts, sizes, weights]

## Hard Rules
[composition rules]

## Visual Strategy
[image handling + visual richness techniques]

## Page Structure
[sections with purposes and visual anchors for each]

## Motion
[2-3 specific animations]

## Do NOT generate
[anti-patterns]

## Responsive
[mobile-first rules]
```
~~~

Keep the brief 60-150 lines. Dense and opinionated beats long and generic.

---

## Preset Palettes

When the user describes a vibe but not specific colors, pick from these curated palettes as a starting point and customize:

**Dark Minimal (Linear/Vercel vibe)**
Background: #09090B, Surface: #18181B, Text: #FAFAFA, Muted: #71717A, Accent: #6366F1, Border: #27272A

**Warm Dark (Notion/Craft vibe)**
Background: #1C1917, Surface: #292524, Text: #FAFAF9, Muted: #A8A29E, Accent: #F59E0B, Border: #44403C

**Light Clean (Stripe/Linear-light vibe)**
Background: #FFFFFF, Surface: #F4F4F5, Text: #18181B, Muted: #71717A, Accent: #2563EB, Border: #E4E4E7

**Bold & Vibrant (Creative/Agency vibe)**
Background: #0F172A, Surface: #1E293B, Text: #F8FAFC, Muted: #94A3B8, Accent: #F43F5E, Border: #334155

**Earthy / Organic**
Background: #FEFCE8, Surface: #FEF9C3, Text: #422006, Muted: #92400E, Accent: #16A34A, Border: #D9F99D

**Cyberpunk / Neon**
Background: #020617, Surface: #0F172A, Text: #E2E8F0, Muted: #64748B, Accent: #22D3EE, Border: #1E293B

These are starting points — always customize to match the specific brand and product.
