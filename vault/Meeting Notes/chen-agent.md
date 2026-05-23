# חן — סוכנת חוקרת הרשת

## Overview

חן היא הסוכנת השלישית בצוות של ראובן שמומשה בפועל (sub-agent של Claude Code ב-`.claude/agents/chen.md`). תפקידה: לקבל בקשה מראובן (נושא / מילות מפתח / סוג מאמר), לחפש ברשת עם WebSearch/WebFetch המובנים של Claude Code (**לא** API חיצוני כמו Tavily/Brave), לסנן לפי קריטריוני איכות, ולשמור את המקור הנבחר כקובץ מוכן ב-`Content/<YYYY-MM-DD>-<slug>.md` שיעל תוכל לעבד. היא מתעדת כל חיפוש ב-`chen/Memory/searches.md` ובודקת שם לפני כל חיפוש חדש כדי למנוע כפילויות (חיפוש תוך 30 יום → שואלת את ראובן אם לעבוד על הקיים). מקבלת 7 כלים: `WebSearch, WebFetch, Read, Write, Edit, Glob, Grep`.

**מיקום בפרויקט:**
- הגדרת הסוכן: `/.claude/agents/chen.md`
- תיקיית עבודה: `/chen/` (`Memory/searches.md` — לוג חיפושים מצטבר)
- פלט: `/Content/<YYYY-MM-DD>-<slug>.md` (קלט ליעל)

**שייכת ל:** ראובן (מנכ"ל) — הוא מנתב אליה בקשות לפי trigger keywords ב-CLAUDE.md, וגם משתמש בה כשלב ראשון ב-pipeline "מאמר מהרשת" (חן → יעל → יובל).

## Open Questions

- האם להוסיף `chen/reference/` לדוגמאות מקורות מועדפים (כמו `yael/reference/` ו-`yuval/reference/`)? לבחון אחרי שמצטברות עבודות — ייתכן שהזיכרון ב-`searches.md` מספיק.
- האם 30 יום הוא הזמן הנכון לסף ה"כבר חיפשתי"? לבחון אחרי שיש מספיק entries בלוג.
- מה קורה כש-WebFetch נכשל על paywall? Flow הנוכחי: עוברת לתוצאה הבאה. אולי כדאי לנסות archive.org כ-fallback בעתיד.
- האם יש עתיד להעביר את חן ל-Tavily/Brave (מפתחות ב-`.env.example`) כשיידרש נפח/מהירות גדולים יותר?

## Session Log

### 2026-05-23 — יצירת חן כ-sub-agent שלישי בצוות [shipped]

- **What was done:** נוצר `.claude/agents/chen.md` עם YAML frontmatter (`name: chen`, `description` עם trigger keywords עברית+אנגלית — חפש/מצא/מחקר/מאמר על/חדש על/מה קורה עם/מקור על + search/find/research/article about/latest on/news on, `tools: WebSearch, WebFetch, Read, Write, Edit, Glob, Grep`) וגוף system prompt בעברית עם flow 8 שלבים: קבלת בקשה → בדיקת זיכרון (Grep על searches.md) → WebSearch (2-4 שאילתות) → WebFetch על המובילות → סינון לפי קריטריוני איכות → שמירה ב-`Content/<YYYY-MM-DD>-<slug>.md` עם frontmatter מלא → תיעוד ב-searches.md → דיווח לראובן. נוצרו `chen/Memory/searches.md` (עם הוראות פורמט) ו-`chen/Memory/.gitkeep`. עודכן CLAUDE.md בארבעה מקומות: רשימת צוות, בלוק ניתוב (הוסרה שורת TODO), section חדש "פייפליין: מאמר מהרשת (חן → יעל → יובל)", ומבנה תיקיות.
- **Decisions:**
  - **WebSearch/WebFetch מובנים בלבד:** חן אינה משתמשת ב-Tavily/Brave (מפתחות ב-`.env.example` נשארים כ-comments לעתיד). הסיבה: כלי Claude Code המובנים מספיקים לצרכים הנוכחיים, ואין צורך ב-API key נוסף.
  - **זיכרון חיפושים:** `chen/Memory/searches.md` הוא הפתרון המרכזי למניעת כפילויות — Grep על מילות המפתח לפני כל חיפוש, entry קבוע אחרי כל חיפוש. 30 יום הוא סף ברירת המחדל (דינמי כגון חדשות → מתעלמת מהסף).
  - **דפוס Graceful Degradation עקבי עם יעל ויובל:** התקדמות > עצירה. תמיד יש תוצר (קובץ ב-Content/ או דיווח ברור מדוע אין). המצב "כל המקורות נמוכי איכות" → שומרת הטוב מבין הרעים + מסמנת בדיווח.
  - **שם קובץ דטרמיניסטי:** `<YYYY-MM-DD>-<slug>.md` עקבי עם דפוס יובל ב-`yuval/outputs/`. slug = 30 תווי הנושא ב-kebab-case.
  - **Frontmatter עשיר בקבצי Content/:** כולל source_url, source_title, source_author, source_date, fetched_at, researcher, quality — יעל מסתמכת עליו.
  - **חן לא קוראת ישירות ליעל:** היא רק מניחה קובץ ב-Content/ ומדווחת לראובן. ראובן מחליט אם ומתי להמשיך לפייפליין.
  - **Pipeline חדש ב-CLAUDE.md:** "פייפליין: מאמר מהרשת (חן → יעל → יובל)" — צעד a-d, כולל התפצלות בין "מצא בלבד" ל-"מצא + שכתב/פרסם".
- **Notes / Caveats:**
  - הסוכנת מקבלת 7 כלים — יותר מיעל (5) ויובל (4), כי WebSearch ו-WebFetch הם כלים נפרדים. Claude Code יאכוף את זה.
  - `chen/Memory/` *לא* הוסף ל-`.gitignore` — לוג החיפושים נשמר ב-Git כחלק מזיכרון הפרויקט.
  - בדיקה חיה (חיפוש אמיתי עם WebSearch) עוד לא בוצעה — תיבדק בסשן הטמעה נפרד.
  - הוסרה שורת "הערה ראשוני" מ-CLAUDE.md — הקובץ כבר לא ראשוני.
- **Related:** [[agents-directory]], [[claude-md]], [[yael-agent]], [[yuval-agent]], [[env-config]]
