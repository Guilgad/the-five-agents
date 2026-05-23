# יובל — סוכן מעצב התמונות

## Overview

יובל הוא הסוכן השני בצוות של ראובן שמומש בפועל (sub-agent של Claude Code ב-`.claude/agents/yuval.md`). תפקידו: לקבל בקשה לתמונה (מהמשתמש או מ-placeholder שיעל השאירה במאמר), לחלץ סגנון מ-`yuval/reference/`, לבנות prompt באנגלית, לקרוא לסקיל [[gpt-image-gen-skill]] (שמשתמש ב-OpenAI Images API עם המודל הקבוע `gpt-image-2`), ולשמור PNG ב-`yuval/outputs/<YYYY-MM-DD>-<slug>.png` + קובץ sibling `.txt` עם ה-prompt המלא (לאיטרציה). מקבל 4 כלים: `Read, Write, Bash, Glob` — Bash הכרחי לקריאת ה-API. המטרה העל-זמנית: עקביות ויזואלית בין כל התמונות בפרויקט.

**מיקום בפרויקט:**
- הגדרת הסוכן: `/.claude/agents/yuval.md`
- תיקיית עבודה: `/yuval/` (`reference/` ל-references סגנון, `outputs/` לתמונות מוגמרות)
- סקיל קשור: `/.claude/skills/gpt-image-gen/SKILL.md`

**שייך ל:** ראובן (מנכ"ל) — הוא מנתב אליו בקשות לפי trigger keywords ב-CLAUDE.md, וגם משתמש בו ב-pipeline המשולב עם [[yael-agent]] לתמונות בתוך מאמרים.

## Open Questions

- האם להוסיף תמיכה ב-Stability AI כ-fallback אם OpenAI נכשל? (יש placeholder ב-.env: `STABILITY_API_KEY` מוערה).
- מה הפורמט המועדף ל-reference: PNG/JPG בלבד, או גם moodboards/קולאז'ים? להחליט כשהמשתמש מתחיל להזין.
- צריך להחליט אם prompts באנגלית הם החלטה נצחית, או לאפשר עברית בעתיד כש-gpt-image מתפתח. כרגע — אנגלית בלבד.
- האם יש צורך ב-cache של תמונות שכבר יוצרו (כדי לחסוך קריאות API חוזרות)? לבחון אחרי שמצטברות עבודות.

## Session Log

### 2026-05-23 — יצירת יובל כ-sub-agent שני בצוות [shipped]

- **What was done:** נוצר `.claude/agents/yuval.md` עם YAML frontmatter (`name: yuval`, `description` עם trigger keywords עברית+אנגלית — "תמונה של/ציור של/תיצור תמונה/איור" + "image of/picture of/generate image/illustration/draw", `tools: Read, Write, Bash, Glob`) וגוף system prompt בעברית עם flow 7 שלבים: סריקת reference → בחירת רכיבי סגנון → ניסוח prompt באנגלית → קריאה ל-gpt-image-gen → שמירת sibling .txt → verification → דיווח. נוצרו תיקיות תפעוליות `yuval/reference/.gitkeep` ו-`yuval/outputs/.gitkeep`. במקביל נוצר הסקיל [[gpt-image-gen-skill]].
- **Decisions:**
  - **Graceful degradation במקביל ליעל:** יובל לא נעצר כש-`yuval/reference/` ריק — עובד best-effort ובדיווח ממליץ להוסיף references. ההחלטה: התקדמות > עצירה (עקבי עם הדפוס של יעל).
  - **Prompts באנגלית בלבד:** gpt-image-2 עובד טוב יותר באנגלית. יובל מתרגם את הבקשה מעברית.
  - **שם קובץ דטרמיניסטי:** `<YYYY-MM-DD>-<slug>.png` עם slug של 30 תווי הבקשה הראשונים ב-kebab-case — קל למצוא ולהפנות מ-MD/HTML.
  - **Sibling `.txt` עם ה-prompt:** קריטי לאיטרציה ("עוד אחת אבל יותר חמה" צריך גישה ל-prompt הקודם).
  - **קו אדום: אל תשנה את שם המודל.** המודל הוא `gpt-image-2` (יצא 2026-04-21). יובל מקבל הוראה מפורשת שאם הקריאה נכשלת — לבדוק key/parameters, לא להחליף ל-`dall-e-3`.
  - **OPENAI_API_KEY כבר ב-.env** — לא נדרש שינוי לקובץ הזה (verified ב-.env:12 ו-.env.example:15 לפני המימוש).
- **Notes / Caveats:**
  - הסוכן מקבל אך ורק 4 כלים — Claude Code יאכוף את זה. אין WebSearch, אין כלי MCP חיצוניים.
  - תיקיית `yuval/outputs/` *לא* הוספה ל-`.gitignore` — תמונות נשמרות ב-Git כדי לאפשר היסטוריה ושיתוף (החלטה עקבית עם `Output/` של יעל).
  - העדכון המקביל ל-`CLAUDE.md` (ראובן) הוסיף את יובל לבלוק הניתוב, יצר section חדש "פייפליין: מאמר עם תמונות (יעל ↔ יובל)" עם 5 שלבים (a-e), ועדכן את בלוק מבנה התיקיות.
  - בדיקה חיה ל-API עוד לא בוצעה — דורש `OPENAI_API_KEY` ממומש. הסקיל מתועד אבל לא הורץ end-to-end.
- **Related:** [[gpt-image-gen-skill]], [[yael-agent]], [[agents-directory]], [[claude-md]], [[skills-catalog]], [[env-config]]
