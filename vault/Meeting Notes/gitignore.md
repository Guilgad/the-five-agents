# .gitignore

## Overview
קובץ המגדיר אילו קבצים ותיקיות מוחרגים מ-Git. הקובץ מגן על סודות (קבצי .env), מנקה קבצי OS (DS_Store, Thumbs.db), ומכין את הפרויקט לשימוש עתידי ב-Node.js ו-Python (node_modules/, __pycache__, .venv).

**מיקום בפרויקט:** `/.gitignore`
**שייך ל:** תשתית הפרויקט (אינו שייך לסוכן ספציפי).

### קטגוריות ה-ignore
| קטגוריה | קבצים |
|---|---|
| סודות | `.env`, `.env.local`, `.env.*.local` |
| קבצי OS | `.DS_Store`, `Thumbs.db`, `desktop.ini` |
| עורכי קוד | `.vscode/`, `.idea/`, `*.swp`, `*.swo` |
| לוגים | `*.log`, `npm-debug.log*`, `yarn-*.log*` |
| Node | `node_modules/` |
| Python | `__pycache__/`, `*.pyc`, `.venv/`, `venv/` |

## Open Questions
- none

## Session Log

### 2026-05-22 — תיעוד ראשוני [planned]
- **What was done:** קריאה של .gitignore ותיעוד הקטגוריות.
- **Decisions:** הכלת Node ו-Python ignore-rules רומזת שייתכן שימוש עתידי בכלים אלה.
- **Notes / Caveats:** vault/ אינו ב-.gitignore — כלומר תכני הוולט נכנסים ל-git.
- **Related:** [[env-config]], [[project-file-mapping]]
