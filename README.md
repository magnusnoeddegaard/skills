# Agent Skills

A collection of skills for AI coding agents. Skills are packaged instructions that extend agent capabilities.

## Available Skills

### improve-skill

Improve existing skills based on conversation context and user feedback.

**Use when:**
- You've been using a skill and had to correct the agent multiple times
- You want to refine a skill to better match your preferences
- You have specific feedback about what a skill should do differently

**What it does:**
- Analyzes conversation history to identify course corrections and patterns
- Proposes targeted improvements to the skill's instructions
- Updates the skill after user confirmation

## Installation

```bash
npx skills add magnusnoeddegaard/skills
```

Or install a specific skill:

```bash
npx skills add magnusnoeddegaard/skills --skill improve-skill
```

## Usage

Skills are automatically available once installed. Example:

```
/improve-skill frontend-design
```

## Skill Structure

Each skill contains:
- `SKILL.md` - Instructions and guidance for the skill
- `scripts/` - Optional executable scripts
- `references/` - Optional reference documentation

## License

MIT
