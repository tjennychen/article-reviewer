---
name: article-reviewer
description: Use when reviewing, improving, or de-fluffing a blog article or long-form content — for WalktheChat, Puzzle Acupuncture, or any brand. Catches AI-generated filler, missing data, voice mismatches, and structural issues through 4 sequential passes.
---

# Article Reviewer

You review and improve blog articles through 4 sequential passes. Each pass focuses on one dimension. Apply corrections after each pass before moving to the next, so each pass works on the cleanest version.

Your job is to improve, not rewrite. Preserve the author's voice and intent. Cut what weakens the article, add what strengthens it.

## Before Starting

1. **Identify the voice skill.** Check who the article is for:
   - WalktheChat / Tingyi Chen → load `jenny-writing-voice` (Channel 3: Blog)
   - Puzzle Acupuncture / Dr. Deb Ma → load `dr-deb-writing-voice` (Channel 4: Blog)
   - Other → ask the user for voice/tone guidance

2. **Read the article.** Read the full article before starting any pass.

---

## Pass 1 — Kill the AI Fluff

The single most important pass. AI-generated content has distinctive tells. Remove all of them.

**Phrases to delete on sight:**

| AI Tell | Why It's Bad |
|---|---|
| "In this article, we will explore..." | Readers don't need a table of contents |
| "It is important to note that..." | If it's important, just say it |
| "It is essential/crucial/fundamental..." | Filler intensifiers that add nothing |
| "In conclusion, it should be highlighted..." | Recap openers that waste the closing |
| "In today's rapidly evolving landscape..." | Generic scene-setting |
| "Let's dive in / Let's explore..." | Performative enthusiasm |
| "Without further ado..." | Throat-clearing |
| "It goes without saying..." | Then don't say it |
| "At the end of the day..." | Cliche |
| "This is a game-changer" | Hype without evidence |
| "Leverage", "utilize", "synergize" | Corporate jargon — use "use", "apply", sharp verbs |

**Structural AI tells to fix:**

- **Single-sentence paragraphs in sequence.** Two or more back-to-back single-sentence paragraphs is a common AI tic. Either combine them or vary the rhythm with a longer analytical block between them.

- **Hollow transitions between sections.** "Now that we've covered X, let's look at Y." Delete these entirely. If the sections are well-structured, the reader doesn't need a guide.

- **Rhetorical question openers.** "Have you ever wondered why...?" "What if there was a better way?" Delete or replace with a direct statement.

- **Symmetric list structures.** When every section follows the exact same template (intro sentence, 3 bullets, concluding sentence), it reads as generated. Vary the structure.

- **Hedging where the author has data.** "This could potentially suggest that..." — if there's data, state the finding directly. Hedging is appropriate only when the evidence genuinely warrants it.

- **Excessive adverbs.** "Really", "very", "truly", "incredibly", "particularly", "notably", "significantly" — cut unless they carry real meaning. Test: does removing the adverb change the sentence's meaning? If not, cut it.

**What to keep:** Direct statements, specific data, concrete examples, the author's genuine voice. Don't strip personality — strip filler.

---

## Pass 2 — Data and Evidence

Every substantive claim should have a specific number, comparison, or source. Vague claims weaken credibility.

**What to look for:**

- **"X is effective/common/growing"** — how effective? What percentage? Compared to what?
- **"Many/most/some people..."** — how many? Is there a study?
- **"Research shows..."** — which research? Link it.
- **Numbers without context.** "85% success rate" means more when compared to an alternative: "85% vs 40% for the control group."
- **Claims without sources.** If a specific stat is cited, it needs a source. If no source exists, flag it to the user rather than inventing one.

**How to fix:**

- If the article already has the data elsewhere, move or reference it.
- If the data exists in the source material, pull it in with proper attribution.
- If data is missing, use `WebSearch` to find it on Google Scholar or PubMed. Search in English (larger literature base), write findings in the article's language.
- If you can't find a reliable source, flag it to the user: "This claim needs a source — I couldn't find one."

**Data integration pattern** (from Jenny's blog style):

Assertion, then specific data, then what it means:
```
Store placement is now a science, not guesswork. Luckin Coffee's success
in saturating school districts (5.8% of locations vs. Starbucks' 0.8%)
stems from computer models that analyze foot traffic, rental costs, and
demographic shifts.
```

Data should serve the narrative, not interrupt it.

---

## Pass 3 — Structure and Clarity

**What to check:**

- **Opening.** Does the article open with stakes, data, or a compelling fact? If it opens with a generality ("X is a growing concern..."), tighten it. The first sentence should make the reader want the second.

- **Section flow.** Can a reader follow from section to section without mental jumps? If a concept is used before it's introduced, reorder.

- **Section headers.** Are they descriptive and interesting? "Price War Dynamics: A Coming Disruption?" beats "Section 3: Pricing." Headers should preview the argument.

- **Paragraph length.** Mix short punchy paragraphs (1-2 sentences) with analytical blocks (3-5 sentences). Never more than 5 sentences. If a paragraph is longer, split it.

- **Redundant sections.** If two sections make the same point, merge or cut one.

- **Closing.** Does it push forward (next steps, implications, what to watch) or just recap what was said? Recaps waste the most powerful position in the article. Instead: "The question isn't whether X, but how quickly."

- **Terms and jargon.** Are technical terms explained the first time they appear? Not over-explained (the reader is smart), but contextualized.

---

## Pass 4 — Voice Check

Compare the article against the relevant voice skill. This pass catches tone mismatches that survived the first three passes.

**For WalktheChat (Jenny):**
- Is the tone conversational authority, not academic?
- Are opinions stated directly, not hedged?
- Are quotes short, attributed, and followed by interpretation?
- Is business jargon used naturally without definition (GMV, ROI, etc.)?
- Are there sharp verbs ("weaponize", "slashed") vs generic ones ("utilize")?

**For Puzzle Acupuncture (Dr. Deb):**
- Is the tone "highly trained doctor talking to a smart friend over coffee"?
- Is the opening punchy (challenges assumptions, raw confessional, perceptual contrast)?
- Are TCM terms followed by translations?
- Is the expertise framed as credential + curiosity + lived experience (not "as an expert in...")?
- Does it arrive at a synthesis — two things that are actually the same puzzle?

**For both:**
- No urgency language ("book now", "act now", "don't miss out")
- No motivational emoji chains
- No "I'm thrilled/excited to share"
- No walls of text — line breaks between ideas
- CTA is soft and inviting, never pushy

---

## Output

After all 4 passes, produce:

1. **Change summary** — organized by pass, focusing on substantive changes. Group minor fixes (typos, removed adverbs). Highlight structural changes and added data.

2. **Revised article** — the full improved article in Markdown.

3. **Unresolved items** (if any) — claims without sources, passages where you're unsure between two approaches, questions for the user.

Save the revised article as `[original-filename]-reviewed.md` in the working directory.
