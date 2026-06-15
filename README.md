# claudeskilltest — medical skills

A small collection of Claude skills for medical/health questions.

- **`symptom-triage`** — structured guidance for user-described symptoms (causes, home care, red flags, disclaimer).
- **`medication-helper`** *(master)* — routes medication questions to the right sub-skill and enforces a consistent safety posture.
  - **`drug-interaction-check`** *(sub)* — pairwise/multi-substance interaction analysis (drugs, supplements, food, alcohol).
  - **`dosage-guide`** *(sub)* — dosing, timing, missed-dose, and population adjustments.

`medication-helper` is the entry point for any drug question; it classifies the request and delegates to `drug-interaction-check` or `dosage-guide`.

## Install

### Claude Code (personal, all projects)
```bash
git clone https://github.com/abhibattini/claudeskilltest.git
mkdir -p ~/.claude/skills
cp -r claudeskilltest/{symptom-triage,medication-helper,drug-interaction-check,dosage-guide} ~/.claude/skills/
```

### Claude Code (project-scoped)
```bash
mkdir -p .claude/skills
cp -r /path/to/claudeskilltest/{symptom-triage,medication-helper,drug-interaction-check,dosage-guide} .claude/skills/
```

### Claude.ai / Claude Desktop
Upload each skill's `SKILL.md` (or zip each folder as `<name>.skill`) via the Skills UI.

> **Note:** `drug-interaction-check` and `dosage-guide` are sub-skills invoked by `medication-helper`. Install all four so routing works correctly.

## Verify
Start Claude Code and try:
- *"I have a sore throat and mild fever for 2 days"* → `symptom-triage`
- *"Can I take ibuprofen with my blood thinner?"* → `medication-helper` → `drug-interaction-check`
- *"How much paracetamol can an adult take per day?"* → `medication-helper` → `dosage-guide`

## Structure
```
symptom-triage/             # standalone
└── SKILL.md
medication-helper/          # master — routes to sub-skills below
└── SKILL.md
drug-interaction-check/     # sub-skill
└── SKILL.md
dosage-guide/               # sub-skill
└── SKILL.md
```

## Disclaimer
General health information only. Not medical advice.
