---
tags: [skill, owner/all-team, trigger/before-declaring-done]
file_path: .claude/skills/verification-before-completion/SKILL.md
owner: ראובן + כל הצוות
trigger: לפני הכרזת סיום — תמיד
---

# Skill: verification-before-completion

## מה הסקיל עושה

מונע הכרזת "הסתיים" לפני אימות אמיתי. מחייב הרצת פקודות ואישור output — לא הנחות. אימות כולל: ריצת טסטים, בדיקת build, בדיקת התנהגות בפועל.

## מתי להפעיל

- **לפני כל הכרזת סיום** — ללא יוצא מן הכלל
- לפני "done", "ready", "complete"
- לפני push/merge

## קבצי עזר

| קובץ | תפקיד |
|------|--------|
| `SKILL.md` | הגדרת הסקיל הראשית |

## למי הוא שייך

**ראובן + כל הצוות** — כולם חייבים לאמת לפני סיום.

## קבצים קשורים

- [[skill-test-driven-development]] — הטסטים שצריך לרוץ
- [[skill-requesting-code-review]] — review לפני סיום
- [[skill-systematic-debugging]] — אם אימות מגלה בעיה
- [[skills-catalog]] — קטלוג כל ה-skills
