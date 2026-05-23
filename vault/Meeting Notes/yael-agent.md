# יעל — סוכנת כתיבת התוכן

## Overview

יעל היא הסוכנת הראשונה בצוות של ראובן שמומשה בפועל (sub-agent של Claude Code ב-`.claude/agents/yael.md`). תפקידה: לקחת מאמרי גלם מ-`Content/`, לשכתב בסגנון הצוות, ולשמור שני פורמטים ב-`Output/` (`.md` + HTML standalone מעוצב לקריאה). הסוכנת מקבלת רק כלי קריאה/כתיבה של קבצים (`Read, Write, Edit, Glob, Grep`) — ללא Bash, ללא WebSearch, ללא API חיצוני. הסגנון נשען על `yael/style-guide.md` ועל דוגמאות ב-`yael/reference/`, שמוזנים ידנית על ידי המשתמש.

**מיקום בפרויקט:**
- הגדרת הסוכן: `/.claude/agents/yael.md`
- תיקיית עבודה: `/yael/` (`style-guide.md`, `reference/`)
- קלט: `/Content/` | פלט: `/Output/`

**שייך ל:** ראובן (מנכ"ל) — הוא מנתב אליה בקשות לפי trigger keywords ב-CLAUDE.md.

## Open Questions

- האם הסגנון של הצוות צריך לעבור לוקליזציה לקהלים שונים (B2B vs. B2C, פוסט בלוג vs. ניוזלטר)? לבחון אחרי שמצטברות עבודות.
- האם להפריד `style-guide.md` לכמה קבצים לפי סוג תוכן, או להישאר במסמך אחד? תלוי בהיקף הסגנון שהמשתמש יזין.
- מה הפורמט המועדף לדוגמאות ב-`yael/reference/`? קובץ-פר-דוגמה, או מסמך אחד עם הפרדות? להחליט כשהמשתמש מתחיל להזין.

## Session Log

### 2026-05-23 — יצירת יעל כ-sub-agent ראשון בצוות [shipped]

- **What was done:** נוצר `.claude/agents/yael.md` עם YAML frontmatter (`name: yael`, `description` עם trigger keywords עברית+אנגלית, `tools: Read, Write, Edit, Glob, Grep` בלבד) וגוף system prompt בעברית. נוצרו תיקיות תפעוליות: `yael/`, `yael/reference/`, `Content/`, `Output/` (כולן עם `.gitkeep`). עודכן `CLAUDE.md` של ראובן עם בלוק "ניתוב לסוכנים" שמתאר מתי להפעיל את יעל.
- **Decisions:**
  - **Graceful degradation במקום עצירה:** יעל לא נעצרת כשחסר style-guide/reference — היא פועלת best-effort ובסיכום ההחזרה לראובן מספקת המלצה ספציפית מה לתעד. ההחלטה: התקדמות > עצירה (החלטת המשתמש בזמן ה-planning).
  - **HTML פלט מינימלי וקריא:** standalone עם CSS inline, RTL, max-width 720px, line-height 1.7. ללא framework חיצוני, ללא תלות CDN.
  - **`yael/style-guide.md` *לא* נוצר כ-stub** — המשתמש יזין בעצמו. עד אז יעל תעבוד עם הלוגיקה המצורפת.
  - **גבולות נוקשים בכתיבה לקבצים:** יעל יכולה לכתוב רק ל-`Output/`. אסור לה לשנות את המקור ב-`Content/` או את ה-style-guide.
- **Notes / Caveats:**
  - הסוכנת מקבלת אך ורק את 5 הכלים שצוינו ב-frontmatter — Claude Code יאכוף את זה ברמת ה-harness. שום Bash / WebSearch / API.
  - תיקיות `Content/` ו-`Output/` *לא* הוספו ל-`.gitignore` — מאמרי גלם ותוצרים יישמרו ב-Git (החלטת המשתמש לטובת היסטוריה ושיתוף).
  - הוסרה ההתנהגות המקורית של "עצירה במקרה של style-guide חסר" אחרי משוב ישיר מהמשתמש בזמן ה-planning.
  - יובל וחן נשארו כ-TODO בבלוק הניתוב של ראובן — יוגדרו בפיצ'רים נפרדים.
- **Related:** [[agents-directory]], [[claude-md]], [[skills-catalog]]

### 2026-05-23 — תוסף: פרוטוקול placeholders לתמונות (חיבור ליובל) [shipped]

- **What was done:** עודכן `.claude/agents/yael.md` בשלושה מקומות: (1) שלב 3.5 חדש — "סימון מקומות לתמונה (placeholders ליובל)" עם פורמט `{{IMAGE_NEEDED: "תיאור..."}}` ורשימת רכיבים שהתיאור צריך לכלול (subject/mood/style/צבעים/קומפוזיציה) + דוגמה; (2) שלב 5 — הוספת שורה לסיכום: "**רשימת placeholders:**" עם המיקומים במאמר; (3) "מה אני לא יודעת" — הבהרה שיעל מסמנת אבל לא יוצרת.
- **Decisions:**
  - **פורמט placeholder אחיד:** `{{IMAGE_NEEDED: "..."}}` — מחרוזת קלה ל-grep ולהחלפה ע"י ראובן בלי לפגוע ב-MD/HTML rendering.
  - **התיאור עשיר מספיק שיובל יוכל לבנות prompt בלי שאלות חוזרות** — חוסך round-trips.
  - **ה-placeholders נשארים גם ב-MD וגם ב-HTML של יעל**, ראובן הוא זה שמחליף אותם בשלב d של ה-pipeline (כדי שיעל לא תצטרך לדעת על נתיבי הפלט של יובל).
- **Notes / Caveats:**
  - יעל עדיין לא יוצרת תמונות בעצמה (אין לה Bash). היא רק מסמנת.
  - אם יעל בוחרת לא להוסיף placeholders למאמר טכני קצר — היא חייבת לציין "ללא תמונות" בסיכום כדי שראובן לא יחפש placeholders חסרים.
  - הפייפליין המלא מתועד ב-[[claude-md]] תחת section "פייפליין: מאמר עם תמונות (יעל ↔ יובל)".
- **Related:** [[yuval-agent]], [[gpt-image-gen-skill]], [[claude-md]], [[agents-directory]]
