# Skills Catalog

## Overview
קטלוג כל ה-Skills (יכולות מותאמות) של הפרויקט, הנמצאים ב-`.claude/skills/`. כל skill הוא קובץ `SKILL.md` (ולפעמים קבצי עזר נוספים) שמגדיר יכולת מיוחדת שהצוות יכול להשתמש בה. ה-Skills מחולקים לשתי קטגוריות: **יכולות תהליך** (איך לעבוד) ו**יכולות Obsidian** (כלים לתיעוד ועריכה).

**מיקום בפרויקט:** `/.claude/skills/`
**שייך ל:** כל הצוות — ראובן הוא הראשי שמפעיל אותם, אך כל הסוכנים יכולים להשתמש.

---

## יכולות תהליך עבודה

### brainstorming
**קובץ:** `.claude/skills/brainstorming/SKILL.md`
**קבצי עזר:** `scripts/` (server.cjs, helper.js, start-server.sh, stop-server.sh, frame-template.html), `spec-document-reviewer-prompt.md`, `visual-companion.md`
**מתי להשתמש:** לפני כל עבודה יצירתית — יצירת פיצ'רים, קומפוננטות, תוסף. חוקר intent, דרישות ועיצוב לפני implementation.
**שייך ל:** ראובן + כל הצוות

---

### dispatching-parallel-agents
**קובץ:** `.claude/skills/dispatching-parallel-agents/SKILL.md`
**מתי להשתמש:** כש-2+ משימות עצמאיות יכולות לרוץ במקביל ללא shared state.
**שייך ל:** ראובן (מחליט מתי להפעיל סוכנים במקביל)

---

### executing-plans
**קובץ:** `.claude/skills/executing-plans/SKILL.md`
**מתי להשתמש:** כשיש תוכנית כתובה לביצוע ב-session נפרד עם review checkpoints.
**שייך ל:** ראובן + כל הצוות

---

### finishing-a-development-branch
**קובץ:** `.claude/skills/finishing-a-development-branch/SKILL.md`
**מתי להשתמש:** כש-implementation הושלמה, הטסטים עוברים, וצריך להחליט על merge/PR/cleanup.
**שייך ל:** ראובן + מי שכותב קוד

---

### receiving-code-review
**קובץ:** `.claude/skills/receiving-code-review/SKILL.md`
**מתי להשתמש:** כשמקבלים code review feedback, לפני implementation של ההצעות — דורש ריגור טכני.
**שייך ל:** ראובן + כל הצוות

---

### requesting-code-review
**קובץ:** `.claude/skills/requesting-code-review/SKILL.md`
**קבצי עזר:** `code-reviewer.md`
**מתי להשתמש:** כשמסיימים tasks, מממשים features גדולות, או לפני merge.
**שייך ל:** ראובן + כל הצוות

---

### subagent-driven-development
**קובץ:** `.claude/skills/subagent-driven-development/SKILL.md`
**קבצי עזר:** `implementer-prompt.md`, `spec-reviewer-prompt.md`, `code-quality-reviewer-prompt.md`
**מתי להשתמש:** כשמבצעים תוכניות implementation עם tasks עצמאיים ב-session הנוכחי.
**שייך ל:** ראובן (מנהל subagents)

---

### systematic-debugging
**קובץ:** `.claude/skills/systematic-debugging/SKILL.md`
**קבצי עזר:** `CREATION-LOG.md`, `condition-based-waiting.md`, `condition-based-waiting-example.ts`, `defense-in-depth.md`, `root-cause-tracing.md`, `find-polluter.sh`, קבצי test-pressure
**מתי להשתמש:** כשנתקלים בבאג, כישלון טסט, או התנהגות לא צפויה — לפני הצעת פתרונות.
**שייך ל:** ראובן + כל הצוות

---

### test-driven-development
**קובץ:** `.claude/skills/test-driven-development/SKILL.md`
**קבצי עזר:** `testing-anti-patterns.md`
**מתי להשתמש:** לפני כתיבת קוד implementation של כל feature או bugfix.
**שייך ל:** ראובן + מי שכותב קוד

---

### using-git-worktrees
**קובץ:** `.claude/skills/using-git-worktrees/SKILL.md`
**מתי להשתמש:** לפני עבודה על feature שצריכה isolation, או לפני executing plans.
**שייך ל:** ראובן + מי שכותב קוד

---

### using-superpowers
**קובץ:** `.claude/skills/using-superpowers/SKILL.md`
**קבצי עזר:** `references/codex-tools.md`, `references/copilot-tools.md`, `references/gemini-tools.md`
**מתי להשתמש:** בתחילת כל שיחה — מאתחל את אופן מציאת ושימוש ב-skills.
**שייך ל:** ראובן (רץ אוטומטית בתחילת session)

---

### verification-before-completion
**קובץ:** `.claude/skills/verification-before-completion/SKILL.md`
**מתי להשתמש:** לפני הכרזה שעבודה הושלמה, תוקנה, או עוברת — דורש הרצת פקודות ואישור output.
**שייך ל:** ראובן + כל הצוות

---

### writing-plans
**קובץ:** `.claude/skills/writing-plans/SKILL.md`
**קבצי עזר:** `plan-document-reviewer-prompt.md`
**מתי להשתמש:** כשיש spec/requirements למשימה מרובת שלבים — לפני נגיעה בקוד.
**שייך ל:** ראובן + כל הצוות

---

### writing-skills
**קובץ:** `.claude/skills/writing-skills/SKILL.md`
**קבצי עזר:** `anthropic-best-practices.md`, `persuasion-principles.md`, `graphviz-conventions.dot`, `render-graphs.js`, `testing-skills-with-subagents.md`, `examples/CLAUDE_MD_TESTING.md`
**מתי להשתמש:** כשיוצרים skills חדשות, עורכים קיימות, או מאמתים לפני deployment.
**שייך ל:** ראובן (מנהל את תשתית ה-skills)

---

## יכולות יצירת תוכן / מדיה

### gpt-image-gen
**קובץ:** `.claude/skills/gpt-image-gen/SKILL.md`
**מתי להשתמש:** כשצריך לייצר תמונה (PNG) מ-prompt טקסטואלי. המעטפת הטכנית לקריאת OpenAI Images API עם המודל `gpt-image-2` (יצא 2026-04-21 — **אסור להחליף לדגם אחר**).
**דורש:** `OPENAI_API_KEY` ב-`.env`. אופציונלי: `jq` + `base64` (Linux/Mac), אחרת Python 3 stdlib (Windows / Git Bash) כ-fallback.
**שייך ל:** [[yuval-agent]] (הצרכן היחיד כרגע — היחיד עם Bash בצוות).
**ראה:** [[gpt-image-gen-skill]] לתיק הנושא המלא.

---

## יכולות Obsidian

### obsidian-bases
**קובץ:** `.claude/skills/obsidian-bases/SKILL.md`
**מתי להשתמש:** עבודה עם קבצי .base, תצוגות table/card, filters, formulas ב-Obsidian.
**שייך ל:** ראובן + כל הצוות (כלי תיעוד)

---

### obsidian-markdown
**קובץ:** `.claude/skills/obsidian-markdown/SKILL.md`
**מתי להשתמש:** עבודה עם קבצי .md ב-Obsidian — wikilinks, callouts, frontmatter, tags, embeds.
**שייך ל:** ראובן + כל הצוות (כלי תיעוד)

---

### obsidian-vault-workflow
**קובץ:** `.claude/skills/obsidian-vault-workflow/SKILL.md`
**מתי להשתמש:** תמיד — בתחילת ובסוף כל משימה. קריאת context וכתיבת session log לוולט.
**שייך ל:** ראובן — זהו ה-protocol המרכזי של זיכרון הפרויקט

## Open Questions
- אילו skills נוספות יידרשו כשהסוכנים (יעל, יובל, חן) יופעלו?
- האם יהיו skills ייחודיות לכל סוכן?

## Session Log

### 2026-05-22 — קטלוג ראשוני של כל ה-skills [planned]
- **What was done:** תיעוד כל 17 ה-skills עם תיאור, מיקום, קבצי עזר, ומתי להשתמש.
- **Decisions:** Skills מחולקות ל"תהליך עבודה" ו"Obsidian" לנוחות ניווט.
- **Notes / Caveats:** חלק מה-skills מכילים קבצי עזר רבים (systematic-debugging, brainstorming) — אלה הכי מורכבות.
- **Related:** [[agents-directory]], [[commands-directory]], [[obsidian-config]], [[project-file-mapping]]

### 2026-05-23 — הוספת gpt-image-gen (סקיל ראשון של יצירת מדיה) [shipped]
- **What was done:** נוסף הסקיל [[gpt-image-gen-skill]] תחת section חדש "יכולות יצירת תוכן / מדיה". הסקיל הוא מעטפת ל-OpenAI Images API עם המודל הקבוע `gpt-image-2`, ומשמש את הסוכן יובל ([[yuval-agent]]).
- **Decisions:** הוספת קטגוריה שלישית בקטלוג ("יצירת תוכן / מדיה") — אזור שיתרחב כשייכנסו עוד סקילים תפעוליים (לעומת תהליך/Obsidian שהם meta).
- **Notes / Caveats:** הסקיל אומת ע"י הופעתו ברשימת ה-skills של Claude Code אחרי השמירה.
- **Related:** [[gpt-image-gen-skill]], [[yuval-agent]], [[agents-directory]]
