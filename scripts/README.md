# Scripts Directory

This directory contains all utility scripts - Python, Bash, Node.js, etc.

## Script Organization

Organize scripts by type or purpose:

```
scripts/
├── automation/        # Automation scripts
├── data/             # Data processing scripts
├── utils/            # General utility scripts
└── temp/             # Temporary one-off scripts (can be deleted)
```

## Script Guidelines

1. Use descriptive filenames
2. Add shebang lines for executable scripts
3. Include comments explaining purpose
4. Make scripts executable when needed: `chmod +x script.sh`

## Running Scripts

```bash
# From workspace root
./scripts/path/to/script.sh

# Or from scripts directory
cd scripts
./path/to/script.sh
```

## Notes

- Scripts here are NOT git-tracked by default
- Commit project-specific scripts within the project in `projects/`
- Use this directory for workspace-wide utilities and one-off scripts
