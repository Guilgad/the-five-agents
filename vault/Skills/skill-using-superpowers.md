---
tags: [skill, owner/reuven, trigger/session-start]
file_path: .claude/skills/using-superpowers/SKILL.md
owner: ראובן
trigger: בתחילת כל שיחה — מאתחל skills
---

# Skill: using-superpowers

## מה הסקיל עושה

מאתחל ומנחה את אופן מציאת ושימוש ב-skills של Claude Code. מאפשר ל-Claude לגלות ולהפעיל כלים של AI שותפים (Gemini, Copilot, Codex) וכלים מיוחדים.

## מתי להפעיל

בתחילת כל שיחה — רץ אוטומטית (כ-SessionStart behavior).

## קבצי עזר

| קובץ | תפקיד |
|------|--------|
| `SKILL.md` | הגדרת הסקיל הראשית |
| `references/codex-tools.md` | כלי OpenAI Codex |
| `references/copilot-tools.md` | כלי GitHub Copilot |
| `references/gemini-tools.md` | כלי Google Gemini |

## למי הוא שייך

**ראובן בלבד** — רץ אוטומטית בתחילת session לטובת כל הצוות.

## קבצים קשורים

- [[settings-json]] — ה-SessionStart hook שמפעיל התנהגויות אוטומטיות
- [[skill-obsidian-vault-workflow]] — סקיל נוסף שרץ בתחילת session
- [[skills-catalog]] — קטלוג כל ה-skills
