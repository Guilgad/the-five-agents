---
tags: [project-file, owner/reuven, type/config]
file_path: .claude/settings.json / .claude/settings.local.json
owner: ראובן
type: config
---

# הגדרות Claude Code (settings.json / settings.local.json)

## מה הקבצים עושים

### `.claude/settings.json`
הגדרות Claude Code ברמת הפרויקט — נכנסות ל-Git ומשותפות לכל המשתמשים.

**תוכן נוכחי — SessionStart Hook:**
```json
{
  "hooks": {
    "SessionStart": [{
      "hooks": [{
        "type": "command",
        "command": "echo ...",
        "shell": "bash",
        "statusMessage": "Loading Obsidian vault protocol..."
      }]
    }]
  }
}
```

**מה ה-hook עושה:** בכל פתיחת session, שולח reminder חובה ל-Claude Code להפעיל את `obsidian-vault-workflow` לפני כל עבודה. זהו מנגנון האכיפה של הפרוטוקול.

### `.claude/settings.local.json`
הגדרות אישיות שלא נכנסות ל-Git (מוחרג).

**תוכן נוכחי — Permissions:**
```json
{
  "permissions": {
    "allow": ["Bash(git push *)"]
  }
}
```

**מה זה עושה:** מאפשר פקודות `git push` ללא אישור ידני בכל פעם.

## למי הם שייכים

**ראובן** — תשתית Claude Code של הפרויקט.
- `settings.json` — ברמת הפרויקט (כל הצוות)
- `settings.local.json` — הגדרות אישיות של המפתח

## קבצים קשורים

- [[CLAUDE-md]] — CLAUDE.md הוא ה"חוקה"; settings.json הוא ה"אכיפה"
- [[skill-obsidian-vault-workflow]] — ה-hook מחייב הפעלת skill זה
- [[github-connection]] — `git push *` הוא הפרמישן שהוגדר ב-settings.local.json
