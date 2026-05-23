# Environment Config

## Overview
שני קבצי הגדרת סביבה של הפרויקט: `.env.example` הוא התבנית הציבורית (נכנסת ל-git), ו-`.env` הוא הקובץ עם הערכים האמיתיים (מוחרג מ-git). ה`.env` מכיל מפתחות API לפי צורכי כל סוכן: Anthropic API לקריאות Claude, OpenAI לתמונות (יובל), וכלי חיפוש (חן). כרגע הכל ריק — המפתחות ממולאים לפי הצורך.

**מיקום בפרויקט:** `/.env`, `/.env.example`
**שייך ל:** כל הצוות — כל סוכן משתמש במפתחות הרלוונטיים לו.

### מפתחות לפי סוכן
| מפתח | סוכן | מתי נדרש |
|---|---|---|
| `ANTHROPIC_API_KEY` | ראובן + כל הצוות | קריאות Anthropic SDK ישירות |
| `OPENAI_API_KEY` | יובל (מעצב) | יצירת תמונות |
| `STABILITY_API_KEY` | יובל (אלטרנטיבה) | יצירת תמונות ב-Stability AI |
| `TAVILY_API_KEY` | חן (חוקרת) | חיפוש אינטרנטי חי |
| `BRAVE_SEARCH_API_KEY` | חן (אלטרנטיבה) | חיפוש אינטרנטי ב-Brave |

## Open Questions
- אילו מפתחות אכן נדרשים כרגע? (כולם מסומנים כ"עתיד")
- האם יהיה קובץ `.env.local` לסביבות שונות?

## Session Log

### 2026-05-22 — תיעוד ראשוני [planned]
- **What was done:** קריאה של .env.example ותיעוד מבנה המפתחות.
- **Decisions:** .env מוחרג מ-git (מופיע ב-.gitignore); .env.example ב-git כתבנית.
- **Notes / Caveats:** אף מפתח אינו ממולא בפועל עדיין — כולם placeholder.
- **Related:** [[gitignore]], [[team-personas]], [[agents-directory]]

### 2026-05-23 — חן משתמשת ב-WebSearch/WebFetch מובנים, לא ב-Tavily/Brave [shipped]
- **What was done:** הובהרה ההחלטה על כלי החיפוש של חן: היא משתמשת ב-WebSearch ו-WebFetch המובנים של Claude Code — **לא** ב-Tavily (`TAVILY_API_KEY`) ולא ב-Brave (`BRAVE_SEARCH_API_KEY`). מפתחות אלו נשארים ב-`.env.example` כ-comments (מוערים) לעתיד.
- **Decisions:** כלי Claude Code המובנים מספיקים לצרכים הנוכחיים. אין צורך ב-API key נוסף לחן. `.env.example` **לא** עודכן — המפתחות נשארים כ-comments למקרה שיעבירו את חן ל-Tavily/Brave בעתיד.
- **Notes / Caveats:** אם בעתיד יידרש נפח גדול / rate limits גבוהים, שווה לשקול Tavily — המפתח כבר מתוכנן ב-.env.example.
- **Related:** [[chen-agent]], [[agents-directory]]
