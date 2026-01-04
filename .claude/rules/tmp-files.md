# Temp File Rules

## Location
Always create temporary files and design docs in `.claude/tmp/` directory.

## Target Files
- Design docs and memos
- Research summaries
- Screenshots
- Temporary scripts
- Debug log files
- Other working files

## Naming Convention
```
.claude/tmp/
├── design/           # Design related
│   └── feature-x-design.md
├── screenshots/      # Screenshots
│   └── ui-check-2024-01-01.png
├── research/         # Research notes
│   └── api-investigation.md
└── scripts/          # Temp scripts
    └── data-migration.rb
```

## Notes
- `.claude/tmp/` is in `.gitignore`, not tracked by git
- Move or document important information to appropriate locations
- Periodically delete unnecessary files
