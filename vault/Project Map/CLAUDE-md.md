---
tags: [project-file, owner/reuven, type/config]
file_path: CLAUDE.md
owner: ראובן
type: config
---

# CLAUDE.md

## מה הקובץ עושה

`CLAUDE.md` הוא קובץ ההוראות הראשי של Claude Code לפרויקט. הוא נקרא אוטומטית בתחילת כל session ומגדיר:

- **זהות**: ראובן הוא המנכ"ל — ה-AI הראשי שמקבל בקשות ומחליט מי מהצוות יבצע אותן
- **הצוות**: יעל (כותבת תוכן), יובל (מעצב תמונות), חן (חוקרת)
- **מבנה התיקיות**: `.claude/agents/`, `.claude/skills/`, `.claude/commands/`
- **פרוטוקול חובה**: להפעיל `obsidian-vault-workflow` בתחילת כל session ולסיים עם Session Log entry

## למי הוא שייך

**ראובן** — מנכ"ל הצוות. CLAUDE.md מגדיר את אישיותו ופרוטוקול העבודה שלו.

> הצוות (יעל, יובל, חן) מוזכר כאן אך עדיין ממתין להגדרת קבצי agent.

## מצב נוכחי

- גרסה ראשונית — תשתית בלבד
- הפרויקט מוגדר כ"מערכת של צוות סוכנים ליצירת תוכן"
- מסומן במפורש כטעון הרחבה עתידית (ניתוב מדויק, עקרונות עבודה)

## קבצים קשורים

- [[settings-json]] — settings.json מחזק את פרוטוקול ה-obsidian-vault-workflow דרך SessionStart hook
- [[agents-directory]] — התיקייה שבה יגורו יעל, יובל וחן
- [[team-personas]] — פרסונות הצוות מפורטות שם
- [[skills-catalog]] — רשימת כל ה-Skills שראובן יכול להפעיל
- [[skill-obsidian-vault-workflow]] — הסקיל שנדרש בכל session

## Session Log

### 2026-05-23 — תיעוד קובץ CLAUDE.md [shipped]
- **What was done:** נוצר קובץ תיעוד ב-vault/Project Map עם הסבר מלא על CLAUDE.md.
- **Decisions:** קובץ זה הוא ה"חוקה" של ראובן — כל שינוי בפרוטוקול העבודה דורש עדכון כאן.
- **Notes / Caveats:** הקובץ מסומן כראשוני — עתיד להתעדכן כשיתווספו הגדרות סוכנים.
- **Related:** [[settings-json]], [[agents-directory]], [[team-personas]]
