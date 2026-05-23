---
tags: [skill, owner/reuven, trigger/parallel-implementation]
file_path: .claude/skills/subagent-driven-development/SKILL.md
owner: ראובן
trigger: כשמבצעים תוכניות implementation עם tasks עצמאיים
---

# Skill: subagent-driven-development

## מה הסקיל עושה

מנחה ניהול subagents לביצוע תוכניות implementation עם tasks עצמאיים ב-session הנוכחי. כולל prompts מוכנים ל-implementer, spec-reviewer ו-code-quality-reviewer.

## מתי להפעיל

- כשיש תוכנית עם tasks עצמאיים הניתנים לביצוע במקביל
- כשהפרויקט גדול מדי לסוכן אחד
- כשרוצים code quality review מובנה

## קבצי עזר

| קובץ | תפקיד |
|------|--------|
| `SKILL.md` | הגדרת הסקיל הראשית |
| `implementer-prompt.md` | prompt לסוכן המממש |
| `spec-reviewer-prompt.md` | prompt לסוכן שסוקר spec |
| `code-quality-reviewer-prompt.md` | prompt לסוקר איכות קוד |

## למי הוא שייך

**ראובן בלבד** — הוא ה-orchestrator שמנהל את ה-subagents.

## קבצים קשורים

- [[skill-dispatching-parallel-agents]] — סקיל דומה לביצוע מהיר יותר
- [[skill-executing-plans]] — ביצוע ליניארי של תוכנית
- [[skill-writing-plans]] — יוצר את התוכנית לפני הביצוע
- [[agents-directory]] — הסוכנים (יעל, יובל, חן) שיהיו ה-subagents
- [[skills-catalog]] — קטלוג כל ה-skills
