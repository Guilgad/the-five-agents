# Project File Mapping

## Overview
מיפוי מלא של כל קבצי הפרויקט the-five-agents לתוך vault/ של Obsidian. הוולט נוצר מאפס ומכיל topic files לכל קטגוריה מרכזית: CLAUDE.md, env-config, .gitignore, .obsidian, agents, commands, כל 17 ה-skills, ופרסונות הצוות. בנוסף, נוצרו שתי תיקיות חדשות: `vault/Project Map/` (תיעוד פרטני לכל קובץ בפרויקט) ו-`vault/Skills/` (קובץ תיעוד לכל אחד מ-17 ה-Skills). הוולט פועל כזיכרון ארוך-טווח של ראובן ושל הצוות.

## Open Questions
- האם יש לוולט לכסות גם קבצי .git/hooks לאחר שיוגדרו hooks?
- כיצד לתעד קבצים חדשים שיתווספו לפרויקט? → הוסף קובץ ל-vault/Project Map/ ועדכן _index.md
- כשיווצרו קבצי agent (יעל, יובל, חן) — יש ליצור עבורם קבצים ב-vault/Project Map/agents/

## Session Log

### 2026-05-22 — יצירת vault ומיפוי קבצי הפרויקט [shipped]
- **What was done:** נוצרו כל תיקיות vault/ (Meeting Notes, Brand Guidelines, Content Briefs, Publishing Log) עם קבצי _index.md. נוצרו 8 topic files ב-Meeting Notes ו-1 ב-Brand Guidelines. כוסו: CLAUDE.md, .env/.env.example, .gitignore, .obsidian/, .claude/agents/, .claude/commands/, .claude/skills/ (17 skills), ופרסונות הצוות.
- **Decisions:** Skills קובצו לקובץ catalog אחד (`skills-catalog.md`) ולא לקבצים נפרדים — כדי למנוע ריבוי קבצים. פרסונות הצוות הולכות ל-Brand Guidelines כי הן עוסקות בזהות ולא בקוד.
- **Notes / Caveats:** .git/ objects ו-hooks לא תועדו (תשתית git רגילה שאינה ייחודית לפרויקט זה). vault/ עצמו אינו ב-.gitignore — תכניו נכנסים ל-git.
- **Related:** [[claude-md]], [[env-config]], [[gitignore]], [[obsidian-config]], [[agents-directory]], [[commands-directory]], [[skills-catalog]], [[team-personas]]

### 2026-05-23 — יצירת vault/Project Map/ ו-vault/Skills/ [shipped]
- **What was done:** נוצרו שתי תיקיות חדשות בוולט: `vault/Project Map/` (8 קבצים) ו-`vault/Skills/` (17+1 קבצים). כל קובץ/תיקייה מרכזית בפרויקט קיבלה קובץ תיעוד עצמאי עם frontmatter, הסבר, בעלות, ותגיות קשורות. כל אחד מ-17 ה-Skills קיבל קובץ תיעוד פרטני.
- **Decisions:** כל קובץ תיעוד כולל frontmatter עם `owner`, `file_path`, ו-`tags` — מאפשר סינון ב-Obsidian. Skills מתועדות עם טבלת קבצי עזר מלאה. הסקיל `obsidian-vault-workflow` קיבל כוכבית ⭐ כי הוא MANDATORY.
- **Notes / Caveats:** הוסף פרוטוקול לשימוש חוזר ב-obsidian-vault-workflow בתחילת כל session — מעוגן גם ב-CLAUDE.md וגם ב-settings.json hook.
- **Related:** [[CLAUDE-md]], [[skills-catalog]], [[agents-directory]], [[vault-directory]]
