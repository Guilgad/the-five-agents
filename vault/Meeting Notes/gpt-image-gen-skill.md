# gpt-image-gen — סקיל יצירת תמונות

## Overview

סקיל מעטפת לקריאת OpenAI Images API. הסקיל הוא **מסמך הוראות** (SKILL.md), לא קוד אוטומטי — הוא מתעד את הפרוטוקול, ה-parameters, ושני מסלולי המימוש (bash+jq וגם Python fallback). מי שמפעיל אותו בפועל הוא [[yuval-agent]] (היחיד עם Bash). הסקיל מקבל `prompt` + `output_path` (+ אופציונלי size/quality/format), שולח POST ל-`https://api.openai.com/v1/images/generations` עם המודל `gpt-image-2`, מפענח את ה-`b64_json` שמוחזר, וכותב PNG ב-output_path. ה-verification (`[ -s "$OUTPUT_PATH" ]`) חובה לפני סיום הקריאה.

**מיקום בפרויקט:** `/.claude/skills/gpt-image-gen/SKILL.md`
**שייך ל:** יובל (הצרכן היחיד כרגע). פוטנציאלית — כל סוכן עם Bash שצריך לייצר תמונה.

## ⚠️ כלל ברזל: המודל הוא `gpt-image-2`

- מודל אמיתי וקיים של OpenAI, שיצא ב-**2026-04-21**.
- הידע הפנימי של מודלי שפה ישנים יותר (cutoff לפני אפריל 2026) לא כולל אותו — **זה לא אומר שהוא לא קיים**.
- אסור לסוכן להחליף ל-`dall-e-3` / `gpt-image-1` / `dall-e-2`. אם הקריאה נכשלת — לבדוק `OPENAI_API_KEY` ו-parameters, **לא** את שם המודל.
- הכלל מתועד באזהרה בולטת ב-SKILL.md ובגבולות של יובל.

## Open Questions

- האם להוסיף לסקיל גם תמיכה ב-`reference_image` (img-to-img) של gpt-image-2 כשנדרש לעדכן תמונה קיימת?
- האם להוסיף batch mode (יצירת 4 וריאציות במכה אחת)?
- jq vs Python — איזה מסלול ייצא ברירת מחדל בפועל? כרגע יובל בוחר לפי הסביבה (Windows → Python, Linux/Mac → jq). אולי כדאי לפשט ל-Python בלבד.

## Session Log

### 2026-05-23 — יצירת הסקיל כחלק מהפעלת יובל [shipped]

- **What was done:** נוצר `.claude/skills/gpt-image-gen/SKILL.md` עם frontmatter תקני (`name` + `description` בלבד, כמו שאר ה-skills בפרויקט — בלי `tools`). תוכן הסקיל: אזהרה בולטת על שם המודל, טבלת parameters, דוגמת bash+curl+jq+base64 מלאה, סקריפט Python fallback עצמאי (stdlib בלבד — `urllib.request`/`json`/`base64`/`os`/`pathlib`), בלוק verification (`[ -s "$OUTPUT_PATH" ]`), וטבלת troubleshooting.
- **Decisions:**
  - **Python fallback מלא, לא רק decode:** הוחלט לכלול סקריפט Python שלם שמטפל ב-HTTP+decode+save, לא רק חתיכת decode קטנה — כי על Windows / Git Bash אין jq, וזה הופך את הסקיל לעצמאי.
  - **stdlib בלבד ב-Python:** בחירה ב-`urllib.request` במקום `requests` כדי לא לדרוש `pip install` (הסקיל אמור לעבוד immediately).
  - **טוען `.env` ב-Python בעצמו:** parser זעיר במקום תלות ב-`python-dotenv`, באותה רוח של "אפס תלות חיצונית".
  - **`[ -s ]` כ-verification מובנה בסקיל:** הסקיל מציין מפורשות שהוא לא נחשב "הצליח" עד שיש קובץ עם תוכן — כדי שיובל לא יוכל לדווח הצלחה על קריאה שכשלה בשקט.
  - **Defaults: 1024x1024, medium, png** — מאזן בין איכות לעלות לרוב השימושים.
- **Notes / Caveats:**
  - בדיקה חיה ל-API עוד לא בוצעה — דורש `OPENAI_API_KEY` ממומש. הסקיל מתועד, מוסכם על הפורמט, אבל לא הורץ end-to-end.
  - הסקיל מופיע ברשימת ה-skills של Claude Code אחרי השמירה (אומת — הופיע בלוג ה-system אחרי הכתיבה).
  - אם יתגלה בעתיד ש-gpt-image-2 דורש פרמטרים נוספים (response_format, n, וכו') — לעדכן את טבלת ה-parameters בסקיל, **לא** לשנות את שם המודל.
- **Related:** [[yuval-agent]], [[skills-catalog]], [[env-config]], [[claude-md]]
