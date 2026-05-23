---
tags: [skill, owner/reuven, trigger/parallel-tasks]
file_path: .claude/skills/dispatching-parallel-agents/SKILL.md
owner: ראובן
trigger: כש-2+ משימות עצמאיות יכולות לרוץ במקביל
---

# Skill: dispatching-parallel-agents

## מה הסקיל עושה

מנחה כיצד להפעיל מספר סוכנים (agents) במקביל כשיש שתי משימות עצמאיות או יותר שאינן דורשות shared state ואין ביניהן תלויות רציפות.

## מתי להפעיל

- כש-2 משימות ניתנות לביצוע עצמאי ללא תלות זו בזו
- כשמקביליות תחסוך זמן משמעותי
- **לא** כשיש תלויות בין המשימות

## קבצי עזר

| קובץ | תפקיד |
|------|--------|
| `SKILL.md` | הגדרת הסקיל הראשית |

## למי הוא שייך

**ראובן בלבד** — הוא ה-CEO שמחליט מתי להפעיל סוכנים במקביל ואיך לחלק את העבודה.

## קבצים קשורים

- [[skill-subagent-driven-development]] — גרסה מורחבת לניהול subagents עם תוכניות
- [[agents-directory]] — הסוכנים שיופעלו במקביל (יעל, יובל, חן)
- [[CLAUDE-md]] — ראובן מוגדר כמחליט מי מהצוות לפעיל
- [[skills-catalog]] — קטלוג כל ה-skills
