---
tags: [skill, owner/all-team, trigger/before-multi-step-task]
file_path: .claude/skills/writing-plans/SKILL.md
owner: ראובן + כל הצוות
trigger: כשיש spec/requirements למשימה רב-שלבית — לפני נגיעה בקוד
---

# Skill: writing-plans

## מה הסקיל עושה

מנחה כתיבת תוכניות implementation מפורטות לפני התחלת עבודה על משימות מורכבות. התוכנית מגדירה שלבים, תלויות, ו-checkpoints — ומשמשת כ"חוזה" לביצוע.

## מתי להפעיל

- כשיש spec או requirements למשימה מרובת שלבים
- **לפני** נגיעה בקוד
- כשמשימה גדולה מדי לסשן אחד

## קבצי עזר

| קובץ | תפקיד |
|------|--------|
| `SKILL.md` | הגדרת הסקיל הראשית |
| `plan-document-reviewer-prompt.md` | prompt לסקירת תוכנית |

## למי הוא שייך

**ראובן + כל הצוות** — כולם יכולים לכתוב תוכניות.

## קבצים קשורים

- [[skill-brainstorming]] — brainstorming לפני כתיבת תוכנית
- [[skill-executing-plans]] — ביצוע התוכנית שנכתבה
- [[skill-subagent-driven-development]] — ביצוע עם subagents
- [[skills-catalog]] — קטלוג כל ה-skills
