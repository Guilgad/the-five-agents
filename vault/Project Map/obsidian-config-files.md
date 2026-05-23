---
tags: [project-file, owner/reuven, type/config]
file_path: .obsidian/
owner: ראובן
type: config
---

# קבצי הגדרות Obsidian (.obsidian/)

## מה התיקייה עושה

`.obsidian/` מכילה את הגדרות האפליקציה Obsidian לפרויקט זה. Obsidian משתמשת בתיקייה זו כדי לזכור את מצב העורך, עיצוב, plugins מופעלים, ועוד.

## קבצים עיקריים

### `app.json`
הגדרות הליבה של Obsidian:
- שפה ופורמט תאריך
- קיצורי מקלדת
- הגדרות editor (spellcheck, line wrap, ...)

### `appearance.json`
הגדרות עיצוב:
- ערכת צבעים (theme)
- גופן
- מצב light/dark

### `core-plugins.json`
רשימת ה-plugins המובנים של Obsidian המופעלים לפרויקט:
- Graph view, Backlinks, Search
- Templates, Daily Notes, ...

### `workspace.json`
**לא נכנס ל-Git** (מוחרג ב-.gitignore) — שומר את מצב הפאנלים הפתוחים.

### `graph.json`
הגדרות תצוגת ה-Graph (עץ הקשרים בין הנוטים).

## למי התיקייה שייכת

**ראובן** — הגדרות העורך לניהול ה-vault. אינן ישירות קשורות לאף סוכן ספציפי.

## קבצים קשורים

- [[vault-directory]] — הוולט שנפתח ב-Obsidian
- [[obsidian-config]] — topic file מסשן קודם עם פרטים נוספים
- [[skill-obsidian-markdown]] — כלי לכתיבה ב-Obsidian Flavored Markdown
- [[skill-obsidian-bases]] — כלי לעבודה עם .base files ב-Obsidian
