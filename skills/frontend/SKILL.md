---
name: frontend
description: >
  Generate production-quality frontend briefs and design systems for AI builder tools (Lovable, Google Stitch, Bolt, v0) and for improving existing projects with Cursor/Claude Code. Use this skill whenever the user wants to create a UI, landing page, dashboard, or web app — whether from scratch or as a redesign. Trigger when the user mentions "vibe coding", "design brief", "design.md", asks to build something visual, or wants to improve the look of an existing frontend. Works for both greenfield projects and incremental redesigns of existing codebases.
---

# Frontend Design Skill

You create opinionated, high-quality frontend briefs that produce results looking like a real designer built them — not a Tailwind UI starter template.

Two modes:
- **New project** → full design.md for AI builder tools (Lovable, Stitch, Bolt, v0)
- **Existing project redesign** → modular section-by-section briefs that respect the current codebase

The skill adapts its output based on which path the user is on.

---

## Step 1: Determine the Path

Before anything else, figure out which mode you're in. If it's not obvious from context, ask:

> "This is a new project from scratch, or you're redesigning / improving something that already exists?"

Then follow the appropriate interview flow.

---

## Step 2: Interview

### 🟢 Path A — New Project (AI builder tool)

Ask these one at a time. Skip what you can infer from context.

1. **What are you building?** Landing page, app UI, dashboard, portfolio, SaaS...
2. **What's the product?** Name, one sentence about what it does and for whom.
3. **Vibe?** References, mood, keywords. "Like Linear", "dark and minimal", "bold agency feel". Links to sites they admire are gold.
4. **Which tool?** Lovable, Stitch, Bolt, v0, Replit, or "any".

After the interview → generate a **full design.md** (see Output: Path A below).

### 🔵 Path B — Existing Project Redesign

Ask these one at a time. Skip what you can infer.

1. **Link to the current site** (or screenshot). What exists today?
2. **What's wrong? What do you want instead?** "Looks cheap", "hero doesn't convert", "feature section is confusing", "want it more like [reference]".
3. **What's the goal?** Sign-ups, purchases, demo bookings, downloads.
4. **What section do you want to tackle first?** Hero? Features? Pricing? Or "you decide".

Then, critically: **read the existing project before generating anything.**

```
Before writing any brief, explore:
- tailwind.config (or CSS variables) → extract existing design tokens
- package.json → understand the real stack (Vue? React? Svelte?)
- Existing components → understand current patterns and naming
- Any agents.md / README → existing project context

DO NOT invent new design tokens if the project already has them.
DO NOT assume React if the project uses Vue or Svelte.
DO NOT generate a monolithic brief — work section by section.
```

After reading the project → generate a **section brief** (see Output: Path B below).

---

## Design Principles

These rules apply to BOTH paths. They are the core of the skill — what prevents generic, template-looking output.

### Composition

```
One composition: The first viewport reads as one complete idea, not a collection of widgets.
Brand first: Product name is hero-level — large, bold, unmistakable. Not tucked in a navbar.
Full-bleed hero: Edge-to-edge visual. No boxed center-column layout on landing pages.
Hero budget: Brand + headline + one supporting sentence + CTA + one visual. Nothing else.
No hero overlays: No floating stat counters, badges, or detached labels on hero imagery.
One job per section: Each section has exactly one purpose and one headline.
Cards: Default is NO cards. Use cards only for things users interact with (pricing tiers, comparisons).
Real visual anchor: Every section needs a visual anchor — product screenshot, code block,
  or styled visual element. Decorative gradients alone don't count.
```

### Anti-Template Techniques

These are the techniques that separate "a designer built this" from "that's a template". Pick 3-5 per project and specify them in the brief.

**Backgrounds with depth:**
- Subtle radial glow behind hero (accent color, 8-12% opacity)
- Alternating section backgrounds (background → surface → background) for rhythm
- Subtle grain/noise texture overlay on dark backgrounds

**Typography as design:**
- Oversized display headings (56-80px) — the headline IS the visual
- One accent-colored word in the headline for emphasis
- Gradient text for hero: white → white/60 fade

**Visual storytelling:**
- Before/after comparisons: show the TRANSFORMATION, not just two code blocks. "Before" should feel painful (code), "After" should feel visual (screenshot/mockup of the result)
- Step-by-step sections: only include steps that actually exist in the product. Don't invent steps to fill a 3-column layout
- Code blocks as design elements: filename tabs, colored status dots, real syntax from the actual product

**Layout with character:**
- Asymmetric layouts for feature sections (image left/text right, then flip)
- Overlapping elements between sections for visual continuity
- Generous whitespace — let sections breathe, don't pack everything tight

### Content Rules

```
Every headline is a statement or action. Never a question.
Lead with what the product DOES, then why it MATTERS.
No mood copy: "Unleash", "Transform", "Supercharge", "Revolutionary" are banned.
No filler: every sentence addresses a specific pain or shows a specific capability.
For app UIs: headings describe what the area IS ("Active Projects", "Search Metrics"),
  not what the user should feel ("Unlock Your Potential").
```

### Before/After Sections — How to Do Them Right

This is where most AI-generated pages fail. The rule:

```
WRONG: Before (code) → After (different code)
  This means nothing to most visitors. Two code blocks look the same.

RIGHT: Before (painful manual code) → After (visual result / clean UI / simple API call)
  The contrast must be VISUALLY obvious, not just textually different.

If the product turns code into visuals: show code → screenshot/mockup.
If the product simplifies code: show long ugly code → short clean code (with line count comparison).
If the product replaces manual work: show the manual process → the automated result.

The "After" must feel like relief. If it doesn't, rethink the comparison.
```

### Anti-Patterns

Include these in every brief:

```
Do NOT generate:
- Generic SaaS card grids as first impression
- Beautiful images with weak brand presence
- Headlines with no clear CTA
- Busy patterns behind body text
- Mood statements repeating across sections ("Discover...", "Transform...")
- Carousels without narrative purpose
- Stacked cards as substitute for actual layout
- Dashboard-card mosaics with thick borders
- Icon rows or feature bento grids as hero content
- Flat solid-color sections with just centered text — add visual depth
- Sections that don't match the actual product (don't invent features or steps)
- More than 2 typefaces without clear reason
```

---

## Output: Path A — Full design.md (New Project)

Generate a single file the user can paste into their AI builder tool. Structure:

~~~
```
## Project
[One sentence: what this is, who it's for, main goal]

## Stack
[React/Vue/Svelte + Tailwind + extras. Ask if unsure — don't guess.]

## Design Tokens
[Full token set with hex values. Use Preset Palettes below as starting points.]

## Typography
[Display, Headline, Body, Code — with sizes, weights, tracking. Max 2 typefaces.]

## Hard Rules
[Composition rules from Design Principles above, adapted to this specific project]

## Visual Strategy
[Which 3-5 anti-template techniques to use. Be specific:
 "Radial glow behind hero CTA using accent at 10% opacity"
 "Gradient text on hero headline: from-white to-white/60"
 "Product screenshot placeholder (aspect-video, max-w-5xl, rounded-xl border)"]

## Page Structure
[Sections with purposes. For each section specify:
 - Headline text
 - What the visual anchor is (screenshot placeholder, code block, styled element)
 - One-sentence description of what this section communicates
 Keep it to 4-5 sections max. More is not better.]

## Motion
[Exactly 2-3 animations. Be specific about what, where, and how.]

## Do NOT generate
[Anti-patterns list, customized to this project]

## Responsive
[Mobile-first rules]
```
~~~

**Length:** 80-150 lines. Dense and opinionated. Not a novel.

### Tool-Specific Adjustments

**Lovable:** Give explicit Tailwind classes. Describe image placeholders with dimensions and labels (user replaces later). Lovable handles long detailed prompts well.

**Google Stitch:** Emphasize mood, visual style, and references. Stitch generates images — describe what you want to see, not just placeholders. "Hero image: abstract 3D rendering of a microcontroller in warm orange lighting."

**Bolt / v0:** Be explicit about React component structure. Name components, describe props.

**Replit Agent:** Break into phases: "Phase 1: layout skeleton. Phase 2: styling and tokens. Phase 3: animations and polish."

---

## Output: Path B — Section Brief (Existing Project)

For redesigns, generate ONE section brief at a time. Structure:

~~~
```
## Section: [Name — e.g., "Hero Redesign"]

### Context
[What exists today and what's wrong with it. Reference actual files/components from the project.]

### Design Direction
[What this section should look like and feel like. Reference EXISTING design tokens from
 the project's Tailwind config — don't invent new ones.]

### Structure
[Exact layout description. What elements, in what order, with what visual weight.]

### Copy
[Actual headline and supporting text. Not placeholder.]

### Visual Anchor
[What's the main visual? Screenshot placeholder with dimensions, code block, styled element.]

### Implementation Notes
[Which existing components to modify or create. File paths if known.
 Specific Tailwind classes using the project's existing token system.
 "Modify components/Hero.vue — replace current centered layout with full-bleed..."]

### Do NOT
[Section-specific anti-patterns. "Don't add a stat counter to the hero.
 Don't use cards for features — use alternating rows."]
```
~~~

**After generating a section brief:**
1. Ask the user to review
2. If approved → they paste into Cursor/Claude Code with their project context
3. Ask: "Which section next?"
4. Repeat until done

This modular approach means each section is tested before moving on. No "generate everything and hope" approach.

---

## Preset Palettes

When the user describes a vibe but not specific colors, use these as starting points and customize. For Path B (existing projects), SKIP THIS — use their existing tokens.

**Dark Minimal (Linear/Vercel)**
Background: #09090B, Surface: #18181B, Text: #FAFAFA, Muted: #71717A, Accent: #6366F1, Border: #27272A

**Warm Dark (Notion/Craft)**
Background: #1C1917, Surface: #292524, Text: #FAFAF9, Muted: #A8A29E, Accent: #F59E0B, Border: #44403C

**Light Clean (Stripe)**
Background: #FFFFFF, Surface: #F4F4F5, Text: #18181B, Muted: #71717A, Accent: #2563EB, Border: #E4E4E7

**Bold & Vibrant (Agency)**
Background: #0F172A, Surface: #1E293B, Text: #F8FAFC, Muted: #94A3B8, Accent: #F43F5E, Border: #334155

**Earthy / Organic**
Background: #FEFCE8, Surface: #FEF9C3, Text: #422006, Muted: #92400E, Accent: #16A34A, Border: #D9F99D

**Cyberpunk / Neon**
Background: #020617, Surface: #0F172A, Text: #E2E8F0, Muted: #64748B, Accent: #22D3EE, Border: #1E293B

---

## Quality Checklist

Before outputting any brief, verify:

**Structure:**
- [ ] Each section has exactly one job
- [ ] Sections match the REAL product — no invented features or steps
- [ ] Cards are justified (not default)
- [ ] Page can be understood by scanning headlines only

**Visual:**
- [ ] Every section has a visual anchor (not just text on flat background)
- [ ] At least 3 anti-template techniques specified
- [ ] Before/after comparisons show visual contrast, not just two code blocks
- [ ] Brand is unmistakable in the first viewport

**Technical:**
- [ ] Stack matches the actual project (not assumed)
- [ ] Design tokens are from the project's config (Path B) or specific hex values (Path A)
- [ ] Typography specifies sizes, weights, tracking
- [ ] Anti-patterns list is included

**Workflow:**
- [ ] User knows what to DO with this file
- [ ] Path A: "paste into [tool name]"
- [ ] Path B: "paste this section brief into Cursor with your project context"

---

## Litmus Test

After generating, mentally ask:
- Is the brand unmistakable in the first screen?
- Is there one strong visual anchor per section?
- Does each section have one job?
- Would a designer look at this brief and think "this person knows what they want"?
- Does the before/after actually show a transformation?
- Would the result look different from a generic Tailwind template?

If any answer is "no" — revise before outputting.
