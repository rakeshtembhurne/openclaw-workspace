# Workspace Organization Summary

This document summarizes the workspace organization setup for web development work.

## Directory Structure

```
openclaw-workspace/
├── projects/              # ALL git repositories and code projects
│   └── README.md         # Instructions for working with projects
├── scripts/              # ALL utility scripts
│   ├── automation/       # Automation scripts
│   ├── data/            # Data processing scripts
│   ├── utils/           # General utility scripts
│   ├── temp/            # Temporary one-off scripts
│   └── README.md        # Instructions for using scripts
├── notes/               # ALL project notes, research, documentation
│   ├── projects/        # Project-specific notes
│   ├── research/        # Research documents
│   ├── ideas/           # Ideas and brainstorming
│   ├── archive/         # Old notes (no longer active)
│   └── README.md        # Instructions for organizing notes
├── memory/              # Daily logs (YYYY-MM-DD.md format)
│   └── heartbeat-state.json  # Track heartbeat check timestamps
├── AGENTS.md            # **UPDATED** - Contains workspace organization rules
├── SOUL.md              # Agent persona and behavior
├── USER.md              # Information about the user
├── IDENTITY.md          # Agent name, vibe, emoji
├── TOOLS.md             # **UPDATED** - Workspace tools and configurations
├── HEARTBEAT.md         # Optional heartbeat checklist
├── CLAUDE.md            # **UPDATED** - Guidance for Claude Code
└── package.json         # Node.js dependencies
```

## Key Rules for AI Assistant

### 1. NEVER Create Files in Root Directory

**ALWAYS** use the appropriate subdirectory:
- Code/Git repo → `projects/`
- Script → `scripts/`
- Note/Doc → `notes/`
- Daily log → `memory/`

### 2. Working with Projects (projects/)

**Clone repos:**
```bash
cd ~/openclaw-workspace/projects
git clone https://github.com/username/repo-name.git
```

**Work on projects:**
```bash
cd projects/<project-name>
git checkout -b feature/<description>
# Make changes
git add .
git commit -m "Clear description"
git push origin feature/<description>
gh pr create --title "Title" --body "Description"
```

**Rules:**
- Always `cd` into project directory before git operations
- Never commit directly to main/master
- Read project's README/CONTRIBUTING.md first
- Test before committing
- Create descriptive PRs

### 3. Creating Scripts (scripts/)

**Place scripts in appropriate subdirectory:**
- `automation/` - Automation scripts
- `data/` - Data processing
- `utils/` - General utilities
- `temp/` - Temporary one-off scripts

**Never create `.py`, `.sh`, `.js` files in root**

### 4. Creating Notes (notes/)

**Place notes in appropriate subdirectory:**
- `projects/` - Project-specific notes
- `research/` - Research documents
- `ideas/` - Ideas and brainstorming
- `archive/` - Old notes

**Naming convention:**
- Project notes: `<project-name>-notes.md`
- Research: `<topic>-research.md`
- Planning: `<project-name>-plan.md`
- Meetings: `<date>-meeting.md`

## Files Updated

### AGENTS.md
Added comprehensive "Workspace Organization (MANDATORY)" section with:
- Directory structure explanation
- Rules for file placement
- Git workflow instructions
- Project organization guidelines

### TOOLS.md
Added "Workspace Tools" section with:
- Git configuration
- Node.js/npm usage
- Python availability
- Playwright and Cheerio information

### CLAUDE.md
Updated with:
- Directory structure overview
- Web development workflow
- Common commands for working with projects
- Script running instructions

## Testing the Setup

To verify the AI assistant follows the rules:

1. **Ask it to clone a repo** - should go to `projects/`
2. **Ask it to write a script** - should go to `scripts/`
3. **Ask it to create notes** - should go to `notes/`
4. **Ask it to make code changes** - should branch from project directory

## Next Steps

1. Clone your existing projects into `projects/`
2. Move any loose scripts to `scripts/`
3. Move any notes to `notes/`
4. Delete or archive old files from root
5. Commit the organized workspace

## Remember

The workspace root should ONLY contain:
- OpenClaw framework files (*.md)
- package.json
- The four main directories (projects/, scripts/, notes/, memory/)

Keep it clean and organized! 🧹
