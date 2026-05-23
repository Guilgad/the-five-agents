---
tags: [skill, owner/reuven, trigger/every-task, mandatory]
file_path: .claude/skills/obsidian-vault-workflow/SKILL.md
owner: ראובן
trigger: תמיד — בתחילת ובסוף כל משימה
priority: MANDATORY
---

# Skill: obsidian-vault-workflow ⭐

## מה הסקיל עושה

**הסקיל המרכזי והחובה של הפרויקט.** מגדיר את פרוטוקול השימוש ב-vault כזיכרון ארוך-טווח. מחייב:

**Phase 1 — לפני כל עבודה:**
1. זיהוי הנושא בביטוי קצר
2. מציאת קובץ הנושא ב-vault
3. קריאת 2-3 Meeting Notes אחרונות
4. דיווח על מה נקרא

**Phase 2 — אחרי כל עבודה:**
1. כתיבת Session Log entry עם: What was done / Decisions / Notes / Related (wikilinks)
2. עדכון Overview אם הנושא התרחב
3. Read-back לאימות הכתיבה

## מתי להפעיל

- **תחילת כל session** (SessionStart hook ב-settings.json)
- **לפני כל משימה**
- **אחרי כל משימה** (לכתיבת Session Log)

> דלג **רק** על שאלות קריאה-בלבד שאינן מייצרות קבצים או החלטות.

## פורמט קובץ נושא

```markdown
# Topic Title

## Overview
תיאור 2-6 משפטים

## Open Questions
- שאלות פתוחות

## Session Log

### YYYY-MM-DD — כותרת [status]
- **What was done:** ...
- **Decisions:** ...
- **Notes / Caveats:** ...
- **Related:** [[wikilinks]]
```

## Status Tags

| תג | משמעות |
|----|--------|
| `[shipped]` | הושלם/הועלה |
| `[wip]` | בתהליך |
| `[planned]` | תוכנן בלבד |
| `[spiked]` | ניסיוני |
| `[debug]` | חקירה בלבד |
| `[reverted]` | בוטל |

## מבנה vault/

```
vault/Meeting Notes/     # קוד, ארכיטקטורה, החלטות
vault/Content Briefs/    # בריפים עריכתיים
vault/Publishing Log/    # פרסומים ותוצאות
vault/Brand Guidelines/  # קול, ויזואלים, טון
vault/Project Map/       # תיעוד קבצי הפרויקט
vault/Skills/            # תיעוד ה-skills
```

## קבצי עזר

| קובץ | תפקיד |
|------|--------|
| `SKILL.md` | הגדרת הסקיל המלאה עם כל הפרוטוקול |

## למי הוא שייך

**ראובן** — הוא אחראי על שמירת הזיכרון של הפרויקט. כל הסוכנים יכתבו Session Logs.

## קבצים קשורים

- [[vault-directory]] — הוולט שהסקיל מנהל
- [[settings-json]] — ה-hook שמחייב הפעלת הסקיל
- [[CLAUDE-md]] — CLAUDE.md מגדיר את חובת הפרוטוקול
- [[skill-obsidian-markdown]] — syntax לכתיבה בוולט
- [[skills-catalog]] — קטלוג כל ה-skills
