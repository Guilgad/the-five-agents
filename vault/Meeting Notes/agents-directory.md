# Agents Directory

## Overview
תיקיית `.claude/agents/` מאחסנת את קבצי ההגדרה של ה-sub-agents בצוות. נכון ל-2026-05-23 מוגדרים בה **יעל** (`yael.md`) — כותבת תוכן, ו-**יובל** (`yuval.md`) — מעצב תמונות. חן עדיין לא הוגדרה. כל קובץ-סוכן הוא markdown עם YAML frontmatter (`name`, `description`, `tools`) ו-system prompt בגוף — זה הפורמט הרשמי של Claude Code sub-agents.

**מיקום בפרויקט:** `/.claude/agents/`
**שייך ל:** ראובן (מנכ"ל) — הוא מנתב אליהם בקשות לפי trigger keywords שבבלוק "ניתוב לסוכנים" ב-CLAUDE.md.

### סטטוס הסוכנים
| קובץ | סוכן | תפקיד | סטטוס |
|---|---|---|---|
| `yael.md` | יעל | כותבת תוכן — שכתוב/עריכה/תרגום/סיכום | ✅ shipped (2026-05-23) — ראו [[yael-agent]] |
| `yuval.md` | יובל | מעצב תמונות — יצירת PNG דרך OpenAI Images API | ✅ shipped (2026-05-23) — ראו [[yuval-agent]] |
| `chen.md` | חן | חוקרת — מידע, מקורות, עובדות | ⏳ TODO |

## Open Questions
- האם הפורמט שבחרנו ליעל (frontmatter + system prompt בעברית) יתאים גם ליובל וחן? כנראה כן, אבל יובל יצטרך תיאור של יכולות ויזואליות וייתכן שדרושים tools נוספים.
- האם יש מצב שבו ראובן מפעיל יותר מסוכן אחד למשימה (pipeline)? לבחון כשיובל וחן יהיו זמינים.

## Session Log

### 2026-05-22 — תיעוד ראשוני [planned]
- **What was done:** תיעוד התיקייה הריקה ואינטנציית השימוש.
- **Decisions:** תיקייה ריקה עם .gitkeep = מקום פנוי מכוון לסוכנים עתידיים.
- **Notes / Caveats:** נכון ל-2026-05-22 אין עדיין קבצי סוכן — יש לעדכן תיק זה עם כל הוספה.
- **Related:** [[claude-md]], [[team-personas]], [[commands-directory]]

### 2026-05-23 — הסוכנת הראשונה (יעל) הוגדרה [shipped]
- **What was done:** נוצר `.claude/agents/yael.md` — sub-agent עם 5 כלים בלבד (`Read, Write, Edit, Glob, Grep`) ו-flow מוגדר לשכתוב מאמרים. נוצרו תיקיות תפעוליות נלוות (`Content/`, `Output/`, `yael/`, `yael/reference/`). עודכן CLAUDE.md עם בלוק ניתוב.
- **Decisions:** הפורמט שאומץ ליעל יוכל לשמש תבנית ליובל וחן. ההחלטה התפעולית של graceful degradation (במקום עצירה כשחסרים קבצי תמיכה) תיבחן גם בסוכנים הבאים.
- **Notes / Caveats:** תיק נושא מפורט נפתח ב-[[yael-agent]] — עדכוני יעל ממשיכים שם, לא כאן.
- **Related:** [[yael-agent]], [[claude-md]]

### 2026-05-23 — הסוכן השני (יובל) הוגדר [shipped]
- **What was done:** נוצר `.claude/agents/yuval.md` — sub-agent עם 4 כלים (`Read, Write, Bash, Glob`). Bash נדרש לקריאת OpenAI Images API דרך הסקיל [[gpt-image-gen-skill]]. Flow של 7 שלבים: סריקת `yuval/reference/` → חילוץ סגנון → ניסוח prompt באנגלית → קריאה לסקיל → שמירת sibling `.txt` → verification → דיווח. נוצרו `yuval/reference/.gitkeep` ו-`yuval/outputs/.gitkeep`. עודכן CLAUDE.md: בלוק ניתוב מורחב, section חדש "פייפליין: מאמר עם תמונות (יעל ↔ יובל)" עם 5 שלבים, ובלוק מבנה תיקיות מעודכן.
- **Decisions:** דפוס ה-graceful degradation של יעל אומץ גם ליובל. הוחלט על trigger keywords עברית+אנגלית (תמונה של/ציור של/תיצור תמונה/איור + image of/picture of/generate image/illustration/draw). שם הקובץ דטרמיניסטי: `<YYYY-MM-DD>-<slug>.png` עם sibling `.txt` לאיטרציה.
- **Notes / Caveats:** תיק נושא מפורט נפתח ב-[[yuval-agent]] — עדכוני יובל ממשיכים שם, לא כאן. נשארה רק חן כ-TODO בצוות.
- **Related:** [[yuval-agent]], [[gpt-image-gen-skill]], [[yael-agent]], [[claude-md]]
