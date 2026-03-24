# 🎯 Skillpack

A curated collection of AI skills — structured prompts and briefs that turn vague ideas into polished results when used with AI builder tools.

**The problem:** You tell Lovable "make me a landing page" and get generic SaaS garbage. You ask Claude to proofread and it gives you a boring "looks good."

**The fix:** Battle-tested skills that know *how* to prompt AI tools properly. Each skill is a structured brief generator — it interviews you, then outputs a ready-to-paste prompt that gets dramatically better results.

## 📦 Skills

| Skill | What it does | Best for |
|-------|-------------|----------|
| [**frontend**](skills/frontend/) | Generates detailed design briefs for AI frontend builders | Lovable, Google Stitch, Bolt, v0, Replit |

> More skills coming: proofreader, copywriter, backend architect...

## 🚀 How to Use

### Option 1: Copy-paste the brief
1. Open a skill's `SKILL.md`
2. Follow the interview structure
3. Fill in your project details
4. Paste the generated brief into your AI tool

### Option 2: Use as a Claude Code skill
```bash
# Add to your Claude Code project
cp -r skills/frontend /path/to/your/project/.claude/skills/
```

### Option 3: Feed directly to an AI assistant
Copy the `SKILL.md` content into your system prompt or paste it at the start of a conversation with any AI assistant — it will follow the skill's workflow.

## 🎨 Frontend Skill — Example

**You say:** "I need a landing page for my AI email marketing tool called MailPilot"

**Skill generates a 80-line brief** with:
- Exact color tokens (`#0A0A0B`, `#6366F1`, etc.)
- Typography specs (Inter, 64px display, -0.02em tracking)
- Page structure (Hero → Product → Social Proof → CTA)
- Composition rules (full-bleed hero, no card grids, one job per section)
- Anti-patterns ("Do NOT generate generic SaaS card grids...")
- Motion specs (2-3 intentional animations)
- Responsive behavior

**You paste it into Lovable** → get a page that looks like a designer built it, not a template.

## 🧠 Philosophy

Each skill follows these principles:

1. **Opinionated > Generic** — specific hex values beat "use dark colors"
2. **Anti-patterns matter** — telling AI what NOT to do is as important as what to do
3. **Interview first** — 2-3 smart questions beat 20 generic ones
4. **Ready to paste** — output goes straight into the tool, no editing needed
5. **Tool-aware** — each skill adapts its output to the target tool (Lovable vs Bolt vs v0)

## 📐 Skill Structure

Every skill follows this format:

```
skills/
└── skill-name/
    └── SKILL.md          # The skill itself (YAML frontmatter + instructions)
```

A `SKILL.md` contains:
- **Frontmatter** — name, description, when to trigger
- **Interview flow** — what to ask the user
- **Brief template** — the structured output format
- **Quality checklist** — verification before output
- **Anti-patterns** — what to avoid

## 🤝 Contributing

Have a skill idea? PRs welcome!

1. Create `skills/your-skill-name/SKILL.md`
2. Follow the structure of existing skills
3. Include: interview flow, output template, anti-patterns, quality checklist
4. Submit a PR with a test example

## 📝 License

MIT — use these skills however you want.

---

*Built with frustration from bad AI outputs and love for good design.*
