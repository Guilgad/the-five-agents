---
tags: [project-file, owner/reuven, type/directory]
file_path: vault/
owner: ראובן + כל הצוות
type: directory
---

# תיקיית ה-Vault (vault/)

## מה התיקייה עושה

`vault/` הוא הזיכרון ארוך-הטווח של הפרויקט — vault של Obsidian שמשמש כ"מוח" של ראובן ושל הצוות. כל session חשוב מתועד כאן, והמידע נשמר ונגיש לסשנים עתידיים.

## מבנה

```
vault/
├── Meeting Notes/          # יומני עבודה, החלטות ארכיטקטורה, תיעוד קוד
│   ├── _index.md           # אינדקס כל נושאי Meeting Notes
│   └── <topic>.md          # קובץ לכל נושא (claude-md, env-config, ...)
│
├── Content Briefs/         # בריפים עריכתיים וקמפיינים
│   └── _index.md
│
├── Publishing Log/         # רישום פרסומים ותוצאות
│   └── _index.md
│
├── Brand Guidelines/       # קול, ויזואלים, טון, UI
│   ├── _index.md
│   └── team-personas.md    # פרסונות הצוות
│
├── Project Map/            # תיעוד קבצי הפרויקט (תיקייה זו)
│   ├── _index.md
│   └── <file>.md           # קובץ לכל קובץ/תיקייה בפרויקט
│
└── Skills/                 # תיעוד כל ה-Skills
    ├── _index.md
    └── skill-<name>.md     # קובץ לכל skill
```

## פרוטוקול השימוש

ה-vault פועל לפי `obsidian-vault-workflow`:
1. **לפני כל עבודה** — קרא את topic file הרלוונטי + 2-3 Meeting Notes אחרונות
2. **אחרי כל עבודה** — כתוב Session Log entry בקובץ הנושא

## למי התיקייה שייכת

**ראובן** — הוא ה-"owner" הראשי, אך כל הצוות (יעל, יובל, חן) ישתמשו בוולט לתיעוד עבודתם.

## קבצים קשורים

- [[skill-obsidian-vault-workflow]] — הסקיל שמנהל את כל הפרוטוקול
- [[obsidian-config-files]] — הגדרות Obsidian שמאפשרות לדפדף בוולט
- [[settings-json]] — ה-SessionStart hook שמחייב שימוש בוולט
