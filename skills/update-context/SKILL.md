---
name: update-context
description: |
  Update context/memory files based on conversation learnings. Use when:
  (1) User says "/update-context" to save new information learned during conversation
  (2) User wants to persist preferences, project details, or personal information to context files
  (3) User asks to "remember this", "save this to context", or "update my claude.md"

  Accepts optional arguments: [filename] [additional instructions]
  - filename: Target file to update (defaults to CLAUDE.md in project root)
  - instructions: What to focus on or specific information to extract

  Examples: "/update-context", "/update-context agents.md", "/update-context claude.md focus on coding preferences"
---

# Update Context

Extract information learned during conversation and persist it to context files for future sessions.

## Arguments

```
/update-context [filename] [instructions]
```

- **filename** (optional): Target file to update. Defaults to `CLAUDE.md` in project root. Common targets: `CLAUDE.md`, `agents.md`, `.claude/settings.md`
- **instructions** (optional): Specific guidance on what to extract or update

## Workflow

### 1. Identify Target File

If filename provided:
- Check if file exists at given path (absolute or relative to project root)
- If not found, search common locations: project root, `.claude/` directory

If no filename:
- Default to `CLAUDE.md` in project root
- If not found, check for `agents.md` or similar context files
- If no context file exists, offer to create `CLAUDE.md`

### 2. Analyze Conversation

Review the conversation history to identify:

**User Information**
- Personal preferences (coding style, tools, frameworks)
- Project-specific details (architecture decisions, conventions)
- Team/organization context
- Communication preferences

**Technical Context**
- Technology stack details
- File structure patterns
- Naming conventions
- Testing approaches
- Deployment configurations

**Workflow Preferences**
- How user likes to receive information
- Level of detail preferred
- Confirmation preferences
- Common tasks or patterns

### 3. Read Existing Context

Read the target file to understand:
- Current structure and sections
- Existing information (avoid duplicates)
- Writing style and format used

### 4. Determine Updates

Compare new information against existing context:
- **Add**: New sections or details not currently captured
- **Update**: Existing sections that need refinement or correction
- **Skip**: Information already present or not worth persisting

If user provided instructions, prioritize extracting that specific information.

### 5. Apply Updates

Preserve existing structure while integrating new information:
- Match the existing formatting style
- Add new sections at logical locations
- Update existing sections in-place when refining
- Use clear, concise language suitable for AI context

### 6. Confirm Changes

Show the user:
- Summary of what was added/updated
- The specific changes made (diff-style or list)

## Guidelines

**What to persist:**
- Stable preferences and patterns (not one-time requests)
- Project architecture and conventions
- Recurring workflows or processes
- Corrections to previous assumptions

**What NOT to persist:**
- Temporary or session-specific details
- Sensitive information (credentials, personal data)
- Information already well-documented in code
- One-off task instructions

**Writing style:**
- Use imperative form for instructions
- Be concise—context files share limited token space
- Structure with clear headers for scannability
- Include examples only when they add clarity

## Examples

### Basic usage
```
User: /update-context
```
→ Scan conversation, identify learnings, update CLAUDE.md

### Specific file
```
User: /update-context agents.md
```
→ Update agents.md with conversation learnings

### With instructions
```
User: /update-context claude.md focus on the database schema we discussed
```
→ Extract database schema details and add to claude.md

### After learning preferences
```
[Conversation where user explained they prefer TypeScript and functional patterns]
User: /update-context
```
→ Add coding preferences section to CLAUDE.md:
```markdown
## Coding Preferences
- Use TypeScript for all new code
- Prefer functional patterns over classes
- Use named exports
```
