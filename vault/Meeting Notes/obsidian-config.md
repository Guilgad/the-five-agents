# Obsidian Config

## Overview
תיקיית `.obsidian/` מכילה את ההגדרות של Obsidian לפרויקט זה. הפרויקט כולו משמש כ-Vault של Obsidian — כלומר ניתן לפתוח את תיקיית השורש ב-Obsidian ולנווט בין כל קבצי ה-MD. ארבעת קבצי ה-JSON מגדירים את ממשק הבסיס ומאפשרים עבודה עם wikilinks, תצוגה, ופלאגינים.

**מיקום בפרויקט:** `/.obsidian/`
**שייך ל:** תשתית הפרויקט — לא לסוכן ספציפי, אלא לסביבת העריכה.

### קבצי ההגדרה
| קובץ | תפקיד |
|---|---|
| `app.json` | הגדרות כלליות של היישום (כרגע ריק `{}`) |
| `appearance.json` | ערכת צבעים, גופנים, ממשק |
| `core-plugins.json` | פלאגינים מובנים מופעלים/כבויים |
| `workspace.json` | מצב פתיחת חלונות ולשוניות אחרון |

## Open Questions
- אילו plugins חיצוניים (community plugins) ייותקנו בעתיד?

## Session Log

### 2026-05-22 — תיעוד ראשוני [planned]
- **What was done:** סריקת .obsidian/ ותיעוד ארבעת קבצי ה-JSON.
- **Decisions:** הפרויקט פועל כ-Obsidian Vault מהשורש — vault/ הוא תיקיית הזיכרון שנגישה ב-Obsidian.
- **Notes / Caveats:** app.json ריק (`{}`), מה שמרמז על הגדרות ברירת מחדל בלבד.
- **Related:** [[skills-catalog]], [[project-file-mapping]]
