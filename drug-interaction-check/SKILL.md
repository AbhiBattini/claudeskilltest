---
name: drug-interaction-check
description: Check interactions between two or more medications, supplements, foods, or alcohol. Use when a user asks "can I take X with Y", "is it safe to combine", "does X interact with Y", "can I drink alcohol while on X", "grapefruit and X", or lists multiple medications and asks about safety. Sub-skill of `medication-helper`.
---

# Drug Interaction Check (Sub-skill)

Sub-skill of `medication-helper`. Analyze whether the substances the user named can be taken together.

## Inputs to Confirm

Before answering, make sure you know:
- Each substance (drug, supplement, food, alcohol) and, if relevant, its dose
- Whether the user is currently taking them or just considering it
- Any high-risk context (pregnancy, age extremes, organ disease, other meds)

If a critical input is missing, ask **one** clarifying question, then proceed.

## Output Format

Respond with these sections in order:

### 🔗 Interaction Summary
One sentence: **None known / Minor / Moderate / Major / Contraindicated**.

### 🧪 Mechanism
- 2–4 bullets explaining *why* the interaction occurs (CYP450, additive sedation, QT prolongation, serotonin syndrome risk, absorption, etc.) — plain English first, technical term in parentheses.

### ⚠️ What to Watch For
- Specific symptoms or lab changes that would indicate the interaction is occurring
- Time window (e.g. "within hours" vs "after days of combined use")

### ✅ Safer Alternatives or Spacing
- If the interaction is dose- or timing-dependent, give the spacing rule (e.g. "separate by 2 hours")
- Suggest a class alternative where appropriate, without naming a specific prescription replacement

### 🚨 Stop & Call a Professional If...
- Red-flag symptoms specific to this combination

End with the master skill's required closing line.

## Special Cases

- **Alcohol + CNS depressants / acetaminophen / metronidazole / nitrates**: always flag as moderate-to-major.
- **Grapefruit + CYP3A4 substrates** (statins, some calcium channel blockers, tacrolimus, etc.): always mention.
- **Serotonergic combinations** (SSRIs + tramadol/MAOIs/triptans/St John's wort): flag serotonin syndrome.
- **Anticoagulants + NSAIDs/aspirin/SSRIs**: flag bleeding risk.
- **Unknown drug name**: do not guess — ask the user to confirm spelling, share the active ingredient, or check the package label. Brand and generic names can differ significantly by region.
