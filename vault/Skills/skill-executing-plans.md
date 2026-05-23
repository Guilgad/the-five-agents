---
tags: [skill, owner/all-team, trigger/after-planning]
file_path: .claude/skills/executing-plans/SKILL.md
owner: ראובן + כל הצוות
trigger: כשיש תוכנית כתובה לביצוע
---

# Skill: executing-plans

## מה הסקיל עושה

מנחה ביצוע של תוכנית implementation קיימת ב-session נפרד עם review checkpoints. מבטיח שהביצוע נאמן לתוכנית ושיש עצירות לאישור בנקודות מפתח.

## מתי להפעיל

- כשיש תוכנית implementation כתובה (מ-writing-plans)
- כשצריך session נפרד עם checkpoints
- לפני התחלת עבודה ארוכה רב-שלבית

## קבצי עזר

| קובץ | תפקיד |
|------|--------|
| `SKILL.md` | הגדרת הסקיל הראשית |

## למי הוא שייך

**ראובן + כל הצוות** — כל מי שמממש תוכנית.

## קבצים קשורים

- [[skill-writing-plans]] — הסקיל שיוצר את התוכנית לפני הביצוע
- [[skill-subagent-driven-development]] — ביצוע עם subagents במקביל
- [[skill-verification-before-completion]] — אימות לפני הכרזת סיום
- [[skills-catalog]] — קטלוג כל ה-skills
