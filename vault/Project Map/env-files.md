---
tags: [project-file, owner/reuven, type/config, sensitive]
file_path: .env / .env.example
owner: ראובן
type: config
---

# קבצי סביבה (.env / .env.example)

## מה הקבצים עושים

### `.env.example`
תבנית לדוגמה של משתני הסביבה הנדרשים לפרויקט. מיועד לשיתוף ב-Git — מראה אילו מפתחות נדרשים **ללא** ערכים אמיתיים.

### `.env`
קובץ הסביבה האמיתי עם ערכי ה-API keys. **לא נכנס ל-Git** (מוחרג ב-.gitignore).

## מפתחות מוגדרים

```
ANTHROPIC_API_KEY=     # מפתח לקריאות ל-Claude API (ראובן, יעל, יובל, חן)
OPENAI_API_KEY=        # מפתח ל-OpenAI (אם נדרש בעתיד)
```

> מפתחות נוספים ייתוספו בהתאם לצרכי כל סוכן.

## למי הם שייכים

**ראובן** — מנהל את התשתית הטכנית. כל הסוכנים (יעל, יובל, חן) יצרכו מפתח ANTHROPIC_API_KEY לפעולתם.

## אזהרת אבטחה

- `.env` לעולם לא יועלה ל-Git
- `.env.example` בטוח לשיתוף — אינו מכיל ערכים אמיתיים
- בדוק `.gitignore` כדי לוודא ש-`.env` מוחרג

## קבצים קשורים

- [[gitignore]] — מוודא ש-.env לא נכנס ל-Git
- [[CLAUDE-md]] — ראובן הוא הבעלים של תשתית ה-API
- [[env-config]] — topic file מסשן קודם עם פרטים נוספים
