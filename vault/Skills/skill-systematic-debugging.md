---
tags: [skill, owner/all-team, trigger/on-bug]
file_path: .claude/skills/systematic-debugging/SKILL.md
owner: ראובן + כל הצוות
trigger: כשנתקלים בבאג, כישלון טסט, או התנהגות לא צפויה
---

# Skill: systematic-debugging

## מה הסקיל עושה

מנחה תהליך דיבוג שיטתי לפני הצעת פתרונות. מתמקד בזיהוי סיבת שורש, לא בפחות-בדיקה של פתרונות מהירים. הכי מורכב מבחינת קבצי עזר.

## מתי להפעיל

- כשנתקלים בבאג
- כשטסט נכשל
- כשיש התנהגות לא צפויה
- **לפני** הצעת כל פתרון

## קבצי עזר

| קובץ | תפקיד |
|------|--------|
| `SKILL.md` | הגדרת הסקיל הראשית |
| `CREATION-LOG.md` | היסטוריית יצירת הסקיל |
| `condition-based-waiting.md` | טכניקת המתנה מבוססת תנאי |
| `condition-based-waiting-example.ts` | דוגמת TypeScript |
| `defense-in-depth.md` | הגנה בשכבות |
| `root-cause-tracing.md` | זיהוי סיבת שורש |
| `find-polluter.sh` | script לאיתור test polluter |
| `test-pressure-1.md` | לחץ טסטים — חלק 1 |
| `test-pressure-2.md` | לחץ טסטים — חלק 2 |
| `test-pressure-3.md` | לחץ טסטים — חלק 3 |
| `test-academic.md` | גישה אקדמית לטסטים |

## למי הוא שייך

**ראובן + כל הצוות**.

## קבצים קשורים

- [[skill-test-driven-development]] — TDD מונע חלק מהבאגים
- [[skill-verification-before-completion]] — אימות לאחר תיקון
- [[skills-catalog]] — קטלוג כל ה-skills
