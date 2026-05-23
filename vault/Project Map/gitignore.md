---
tags: [project-file, owner/reuven, type/config]
file_path: .gitignore
owner: ראובן
type: config
---

# .gitignore

## מה הקובץ עושה

`.gitignore` מגדיר אילו קבצים ותיקיות **לא** יכנסו ל-Git. מגן על:

- **סודות**: `.env`, `*.pem`, `*.key` — לא לשתף מפתחות API
- **קבצי OS**: `.DS_Store`, `Thumbs.db`, `desktop.ini`
- **קבצי עורך**: `.vscode/`, `.idea/`, `*.swp`
- **לוגים**: `*.log`, `logs/`, `npm-debug.log*`
- **תלויות**: `node_modules/`, `__pycache__/`, `*.pyc`
- **builds**: `dist/`, `build/`, `.cache/`

## למי הוא שייך

**ראובן** — תשתית הפרויקט. נוצר אחד פעם ונשמר לאורך החיים של הפרויקט.

## חשוב לזכור

- vault/ **כן** נכנס ל-Git (אינו מוחרג) — זהו כוונה מכוונת
- `.env` מוחרג — בדוק שהוא רשום לפני push

## קבצים קשורים

- [[env-files]] — .env הוא הדוגמה המרכזית לקובץ שחייב להיות ב-.gitignore
- [[github-connection]] — מצב חיבור ה-Git של הפרויקט
- [[gitignore]] — topic file מסשן קודם
