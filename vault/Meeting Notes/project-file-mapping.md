# Project File Mapping

## Overview
מיפוי מלא של כל קבצי הפרויקט the-five-agents לתוך vault/ של Obsidian. הוולט נוצר מאפס בסשן זה ומכיל topic files לכל קטגוריה מרכזית: CLAUDE.md, env-config, .gitignore, .obsidian, agents, commands, כל 17 ה-skills, ופרסונות הצוות. הוולט פועל כזיכרון ארוך-טווח של ראובן ושל הצוות.

## Open Questions
- האם יש לוולט לכסות גם קבצי .git/hooks לאחר שיוגדרו hooks?
- כיצד לתעד קבצים חדשים שיתווספו לפרויקט?

## Session Log

### 2026-05-22 — יצירת vault ומיפוי קבצי הפרויקט [shipped]
- **What was done:** נוצרו כל תיקיות vault/ (Meeting Notes, Brand Guidelines, Content Briefs, Publishing Log) עם קבצי _index.md. נוצרו 8 topic files ב-Meeting Notes ו-1 ב-Brand Guidelines. כוסו: CLAUDE.md, .env/.env.example, .gitignore, .obsidian/, .claude/agents/, .claude/commands/, .claude/skills/ (17 skills), ופרסונות הצוות.
- **Decisions:** Skills קובצו לקובץ catalog אחד (`skills-catalog.md`) ולא לקבצים נפרדים — כדי למנוע ריבוי קבצים. פרסונות הצוות הולכות ל-Brand Guidelines כי הן עוסקות בזהות ולא בקוד.
- **Notes / Caveats:** .git/ objects ו-hooks לא תועדו (תשתית git רגילה שאינה ייחודית לפרויקט זה). vault/ עצמו אינו ב-.gitignore — תכניו נכנסים ל-git.
- **Related:** [[claude-md]], [[env-config]], [[gitignore]], [[obsidian-config]], [[agents-directory]], [[commands-directory]], [[skills-catalog]], [[team-personas]]
