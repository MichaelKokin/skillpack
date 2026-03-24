# skillpack

Open-source skills for AI-powered development. First up: a frontend design system generator.

## 🎨 Frontend Design Skill

Generates a reusable `design.md` — a design system document with tokens, component patterns, composition rules, and anti-patterns. Based on [OpenAI's frontend design guide](https://developers.openai.com/blog/designing-delightful-frontends-with-gpt-5-4).

Works with: **Lovable, Google Stitch, Bolt, v0, Cursor, Claude Code.**

### How it works

**Quick interview** — 4 questions:
1. 🏗 What are you building? (landing, app, dashboard...)
2. 🏷 What's the product?
3. 🎨 Vibe? ("dark minimal", "like Linear", "bold agency" — or a link to a site you admire)
4. 🔧 Which tool? (Lovable, Stitch, Bolt, v0)

Skips questions it can already infer from context.

**Three paths:**
- 🟢 **New project** → full design system from scratch
- 🔵 **Redesign with codebase** → reads your `tailwind.config`, respects existing tokens
- 🟣 **Redesign without codebase** → analyzes current site (Tilda, Webflow, etc.), evolves brand into a system

### What you get

A `design.md` with:

| Section | What's inside |
|---------|--------------|
| **Color tokens** | Specific hex values — background, surface, text, muted, accent, border |
| **Typography** | Fonts, sizes, weights, tracking, line-heights — by role (Display, H1, Body, Caption) |
| **Spacing & Radii** | Section gaps, content gaps, border-radius tokens |
| **Shadows** | Elevation levels with actual CSS values |
| **Composition rules** | How to structure sections, hero constraints, card usage rules |
| **Visual techniques** | 3-5 specific anti-template techniques with CSS-level detail |
| **Component patterns** | CTA buttons, nav, portfolio cards, image placeholders |
| **Anti-patterns** | What the AI tool should NOT generate |
| **Page blueprint** | Optional section skeleton — structure without copywriting |

**6 preset palettes** when you describe a vibe:

| Palette | Think... |
|---------|----------|
| Dark Minimal | Linear, Vercel |
| Warm Dark | Notion, Craft |
| Light Clean | Stripe |
| Bold & Vibrant | Agency |
| Earthy | Wellness, eco |
| Cyberpunk | Web3, gaming |

### ⚠️ What design.md is (and isn't)

**design.md is a foundation, not a finished site.**

It gives AI tools the right constraints — colors, fonts, spacing, composition rules, things to avoid. Without it, you get generic Tailwind UI templates. With it, you get a consistent visual system.

But it won't produce a polished result from one prompt.

| What design.md does | What still needs you |
|---|---|
| ✅ Consistent tokens across all pages | 🖼 Real images (placeholders are just placeholders) |
| ✅ Typography system | ✍️ Your own copy and headlines |
| ✅ Component specs with hover states | 🔧 Font loading (some AI tools ignore custom fonts) |
| ✅ Anti-patterns that block generic output | 📐 Layout tweaks (alignment, spacing) |
| ✅ Reusable for every page you build | 🔄 Iteration — first result always needs work |

**The real workflow:**
1. Generate `design.md`
2. Paste into Lovable/Stitch/v0 → version 1 (it WILL have issues)
3. Replace placeholders with real images
4. Rewrite generated copy
5. Fix what the tool got wrong
6. For the next page → "use my design.md" → same style, no starting over

This is how design systems work in production — they don't eliminate iteration, they make it faster and consistent.

---

## Examples

- [`examples/kachkovenko/`](examples/kachkovenko/) — Design agency redesign (Path C: Tilda → new design system)

## Usage

### Claude Code
```bash
cp -r skills/frontend your-project/.claude/skills/frontend
```

### Manual
Read [`skills/frontend/SKILL.md`](skills/frontend/SKILL.md) and follow the interview. Output is a markdown file you paste anywhere.

### Any AI assistant
Copy `SKILL.md` into the conversation → follow the flow → get your design.md.

## Coming Soon

More skills based on real workflows — proofreader, backend architecture, and others.

## License

MIT
