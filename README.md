# Article Reviewer

A Claude Code skill for de-fluffing blog articles and long-form content. Five sequential passes, each focused on one dimension. Apply corrections after each pass before the next, so each pass works on the cleanest version.

The job is to improve, not rewrite. Preserve voice. Cut what weakens the article, add what strengthens it.

See [`SKILL.md`](./SKILL.md) for the full pass-by-pass reference.

## When to use it

You have a draft article (yours, a teammate's, an LLM-generated first pass) and you want it to:

- Rank for a target keyword without reading like SEO sludge.
- Lose the AI tells (corporate filler, hollow transitions, hedge words, throat-clearing intros).
- Make every claim specific. Numbers, comparisons, sources.
- Match a brand voice or author voice you can describe.

Skip this skill if the article is a personal essay where the "fluff" is the point, or if you don't have a target keyword and you're just drafting freeform.

## What it catches

The five passes:

1. **Keyword Targeting.** Title, first 100 words, headers, body density, closing, and off-target drift. Runs first so every later pass works on a piece already aligned to what it should rank for.
2. **AI Fluff.** A table of phrases to delete on sight, plus structural tells (sequential one-sentence paragraphs, hollow transitions, rhetorical question openers, symmetric list templates, hedge words, dead adverbs).
3. **Data and Evidence.** Vague claims get specific numbers. Stats without sources get sourced or flagged. The pattern: assertion, specific data, what it means.
4. **Structure, Clarity, Repetition.** Opening, flow, header phrasing, paragraph rhythm, redundant sections, repeated links, unsupported claims, closing that pushes forward instead of recapping.
5. **Voice Check.** The article walked against a voice profile, brand guide, or sample text you provide upfront. Plus universal checks (no urgency language, no motivational emoji, no "I'm thrilled to share," soft CTAs).

## Install

Global (works across all Claude Code sessions):

```bash
mkdir -p ~/.claude/skills/article-reviewer
curl -fsSL https://raw.githubusercontent.com/tjennychen/article-reviewer/main/SKILL.md \
  -o ~/.claude/skills/article-reviewer/SKILL.md
```

Per project:

```bash
mkdir -p .claude/skills/article-reviewer
curl -fsSL https://raw.githubusercontent.com/tjennychen/article-reviewer/main/SKILL.md \
  -o .claude/skills/article-reviewer/SKILL.md
```

Verify by asking Claude in any session: "Review this article using the article-reviewer skill."

## How it works in a session

Before any pass runs, the skill asks you for two things:

1. **Voice.** A voice profile, brand guide, sample articles, or direct guidance ("conversational authority, no hedging, business jargon used naturally"). If you don't have one, the skill will pause and ask. It won't guess.
2. **Target keyword(s).** One primary keyword, 1 to 3 secondary. These anchor Pass 1.

Then it reads the full article, runs the five passes in order, and produces:

- A change summary grouped by pass, with a keyword audit table at the top.
- The revised article in Markdown, saved as `[original-filename]-reviewed.md`.
- Unresolved items: missing sources, judgement calls flagged for you.

## License

MIT
