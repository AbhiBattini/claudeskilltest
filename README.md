# symptom-triage skill

A Claude skill that triages user-described symptoms and returns structured health guidance (possible causes, home care, red flags, disclaimer).

## Install

### Claude Code (personal, all projects)
```bash
git clone https://github.com/abhibattini/claudeskilltest.git
mkdir -p ~/.claude/skills
cp -r claudeskilltest/symptom-triage ~/.claude/skills/
```

### Claude Code (project-scoped)
```bash
mkdir -p .claude/skills
cp -r /path/to/claudeskilltest/symptom-triage .claude/skills/
```

### Claude.ai / Claude Desktop
Upload `symptom-triage/SKILL.md` (or zip the `symptom-triage/` folder as `symptom-triage.skill`) via the Skills UI.

## Verify
Start Claude Code and ask something like *"I have a sore throat and mild fever for 2 days"* — the skill should activate and respond in the four-section format.

## Structure
```
symptom-triage/
└── SKILL.md   # frontmatter (name, description) + instructions
```

## Disclaimer
General health information only. Not medical advice.
