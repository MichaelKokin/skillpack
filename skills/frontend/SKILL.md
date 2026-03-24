---
name: frontend
description: >
  Generate production-quality frontend briefs and prompts for AI builder tools like Lovable, Google Stitch, Bolt, v0, Replit Agent, and similar platforms. Use this skill whenever the user wants to create a UI, landing page, dashboard, web app, or any frontend project using an AI code generation tool. Also trigger when the user mentions "vibe coding", asks to "write a prompt for Lovable/Stitch/Bolt/v0", wants to build something visual, or needs help describing a frontend project to an AI tool. Even if the user just says "make me a landing page" or "I need a dashboard" — this skill helps craft the perfect brief so the AI tool produces polished, professional results instead of generic templates.
---

# Frontend Brief Generator

You help users create detailed, opinionated frontend briefs that produce stunning results when fed into AI builder tools (Lovable, Google Stitch, Bolt, v0, Replit Agent, etc.).

The core insight: AI builder tools produce dramatically better output when given a structured, opinionated brief rather than a vague description. A prompt like "make me a landing page for my SaaS" produces generic garbage. A brief that specifies composition, typography strategy, color tokens, section purposes, and anti-patterns produces something that looks like a real designer built it.

## How This Works

You interview the user, then generate a ready-to-paste prompt. The interview is quick — 2-3 focused questions, not a 20-question survey. You should infer as much as possible from context and fill in smart defaults.

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

### Section 3: Layout & Composition Rules

These rules prevent the AI tool from falling into common traps. Include them verbatim — they're battle-tested.

```
## Composition Rules
- The first viewport must read as ONE complete idea — not a collection of components
- Brand/product name is hero-level, not buried in a nav bar
- Full-bleed hero: edge-to-edge visuals, no boxed center-column layout
- Hero budget: brand + headline + one supporting sentence + CTA + one visual. That's it.
- No floating badges, detached labels, or overlays on hero imagery
- No cards by default. Use cards ONLY for interactive elements (pricing tiers, feature comparisons users click through)
- Each section has exactly ONE job and ONE headline
- Every image must show product or context — no decorative stock photography
- No pill clusters, stat strips, icon grids, or visual clutter
- No filler copy. Every word earns its place.
- Maximum one accent color unless a strong design system justifies more
```

### Section 4: Page Structure

Adapt this based on project type.

**For Landing Pages:**
```
## Page Structure
1. Hero — Establish brand identity and core promise. Full-bleed visual. One CTA.
2. Supporting Visual — Show the product in context (screenshot, demo, lifestyle image)
3. Product Detail — Explain the core offering. 2-3 features max, not a feature dump.
4. Social Proof — Testimonials, logos, or metrics. Keep it tight.
5. Final CTA — Repeat the call to action with urgency or incentive.
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

## Utility Copy Rules
- Section headings describe what the area IS or what users DO there
- Good: "Active Projects", "Search Metrics", "Plan Status"
- Bad: "Unlock Your Potential", "Discover Insights", "Your Journey"
- Prioritize orientation, status, and action over mood and brand voice
```

### Section 5: Motion & Animation

```
## Motion
Ship exactly 2-3 intentional motions:
1. One entrance animation in the hero (fade-up + scale, or text reveal)
2. One scroll-linked effect (parallax, sticky section, or reveal-on-scroll)
3. One interaction micro-animation (button hover, card lift, or toggle)

Use Framer Motion for: section reveals, shared layout transitions, scroll-linked effects.
Keep fixed/floating elements from overlapping text or buttons across screen sizes.
No decorative animation. Every motion must reinforce hierarchy or provide feedback.
```

### Section 6: Anti-Patterns (Rejection Checklist)

Always include this — it's the most impactful section for preventing bad output.

```
## Do NOT generate:
- Generic SaaS card grids as the first impression
- Beautiful hero images with weak or missing brand presence
- Strong headlines with no clear action/CTA
- Busy imagery or patterns behind text
- Repeating section mood statements ("Unleash...", "Discover...", "Transform...")
- Carousels without narrative purpose
- Stacked cards as a substitute for actual layout design
- Decorative shadows or glassmorphism without purpose
- Icon rows or feature grids as hero content
- Split-screen hero where the text side is cluttered
- Gradients that fight with text readability
- More than 2 typefaces without strong justification
```

### Section 7: Responsiveness

```
## Responsive Behavior
- Mobile-first: design for 375px, then scale up
- Hero text should remain readable without horizontal scroll on mobile
- Navigation collapses to hamburger or bottom nav on mobile
- Touch targets minimum 44x44px
- Images use aspect-ratio containers to prevent layout shift
```

---

## Adapting to the Target Tool

Slight adjustments based on which AI tool the user is targeting:

**Lovable**: Loves detailed prompts. Include all sections. Lovable responds well to explicit Tailwind class suggestions (e.g., "use `bg-zinc-950` for background"). You can be very specific about layout.

**Google Stitch**: More visual/design-oriented. Emphasize the design tokens, mood, and visual references. Stitch works well with style descriptions ("dark, minimal, with electric blue accents and generous whitespace").

**Bolt / v0**: These tools handle React + Tailwind natively. Be explicit about component structure. You can suggest specific component breakdowns (e.g., "Hero component with full-width background image, overlay gradient, and centered text block").

**Replit Agent**: Prefers step-by-step structure. Break the brief into clear phases: "First build the layout skeleton, then add styling, then add animations."

If the user says "any" or doesn't specify, default to the Lovable format (most detailed).

---

## Quality Checklist

Before outputting the final brief, verify:
- [ ] Brand/product is unmistakable in the first viewport
- [ ] There's one strong visual anchor (not a collage)
- [ ] Page can be understood by scanning headlines alone
- [ ] Each section has exactly one job
- [ ] Cards are justified (not default)
- [ ] Motion serves hierarchy, not decoration
- [ ] No filler copy or placeholder text
- [ ] Color tokens are specific hex values, not "blue" or "dark"
- [ ] Typography specifies sizes, weights, and tracking
- [ ] Anti-patterns section is included

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

## Composition Rules
[rules]

## Page Structure
[sections with purposes]

## Motion
[2-3 specific animations]

## Do NOT generate
[anti-patterns]

## Responsive
[mobile-first rules]
```
~~~

Keep the brief focused — it should be 60-120 lines, not a novel. AI tools work best with dense, opinionated instructions, not exhaustive documentation.

---

## Preset Palettes

When the user describes a vibe but not specific colors, pick from these curated palettes as a starting point and adjust:

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

These are starting points — always customize to match the specific brand and product context.
