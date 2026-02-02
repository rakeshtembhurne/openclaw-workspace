# TOOLS.md - Local Notes

Skills define *how* tools work. This file is for *your* specifics — the stuff that's unique to your setup.

## What Goes Here

Things like:
- Camera names and locations
- SSH hosts and aliases
- Preferred voices for TTS
- Speaker/room names
- Device nicknames
- Anything environment-specific

## Workspace Tools

### Git
- **GitHub CLI**: Available for creating PRs (`gh pr create`)
- **Default branch**: Usually `main` or `master` - check each project
- **Branch naming**: `feature/<description>`, `bugfix/<description>`, `hotfix/<description>`

### Node.js/npm
- **Package manager**: npm (available in workspace)
- **Install dependencies**: `npm install` (run from project directory)
- **Run scripts**: `npm run <script-name>` (check package.json)

### Python
- **Python 3**: Available via `python3` command
- **Pip**: Available for package installation

### Playwright (for web scraping)
- **Installed**: Version ^1.58.1
- **Use**: Browser automation for government sites and data extraction
- **Run from**: `scripts/` directory

### Cheerio (for HTML parsing)
- **Installed**: Version ^1.2.0
- **Use**: HTML parsing for web scraping tasks

## Examples

```markdown
### Cameras
- living-room → Main area, 180° wide angle
- front-door → Entrance, motion-triggered

### SSH
- home-server → 192.168.1.100, user: admin

### TTS
- Preferred voice: "Nova" (warm, slightly British)
- Default speaker: Kitchen HomePod
```

## Why Separate?

Skills are shared. Your setup is yours. Keeping them apart means you can update skills without losing your notes, and share skills without leaking your infrastructure.

---

Add whatever helps you do your job. This is your cheat sheet.
