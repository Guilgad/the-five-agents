---
tags: [skill, owner/all-team, trigger/before-creative-work]
file_path: .claude/skills/brainstorming/SKILL.md
owner: ראובן + כל הצוות
trigger: לפני כל עבודה יצירתית
---

# Skill: brainstorming

## מה הסקיל עושה

מסייע להפוך רעיונות לעיצובים מלאים ו-specs לפני כל implementation. מנהל דיאלוג עם המשתמש כדי להבין intent, דרישות ועיצוב — ורק אחרי אישור עיצוב מותר להתחיל לממש.

**Hard Gate:** אסור לכתוב קוד, scaffold פרויקט, או לנקוט כל פעולת implementation לפני שהמשתמש אישר את העיצוב.

## מתי להפעיל

- לפני יצירת פיצ'ר חדש
- לפני הוספת קומפוננטה
- לפני כל שינוי משמעותי בהתנהגות
- **גם לפרויקטים "פשוטים"** — פשטות אינה פטור מעיצוב

## קבצי עזר

| קובץ | תפקיד |
|------|--------|
| `SKILL.md` | הגדרת הסקיל הראשית |
| `visual-companion.md` | הנחיות לתמיכה ויזואלית בעיצוב |
| `spec-document-reviewer-prompt.md` | prompt לסקירת spec documents |
| `scripts/server.cjs` | שרת עזר לתצוגה ויזואלית |
| `scripts/helper.js` | פונקציות עזר |
| `scripts/frame-template.html` | תבנית HTML לפריים |
| `scripts/start-server.sh` | הרצת השרת |
| `scripts/stop-server.sh` | עצירת השרת |

## למי הוא שייך

**ראובן** — מחליט מתי לקרוא לסקיל. **כל הצוות** — כולם יכולים להשתמש בו.

## קבצים קשורים

- [[skill-writing-plans]] — לאחר brainstorming לעיתים כותבים תוכנית
- [[skill-executing-plans]] — ביצוע התוכנית שנוצרה
- [[skill-subagent-driven-development]] — ביצוע עם subagents
- [[skills-catalog]] — קטלוג כל ה-skills
