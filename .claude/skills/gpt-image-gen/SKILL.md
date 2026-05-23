---
name: gpt-image-gen
description: Generate an image via OpenAI Images API using the gpt-image-2 model. Use whenever the team needs a PNG produced from a text prompt. Wraps the curl call, decoding, and file save; consumer (typically יובל) supplies prompt + output_path.
---

# gpt-image-gen Skill

מעטפת קריאה ל-OpenAI Images API. נותן prompt → מקבל קובץ PNG בנתיב שביקשת.

הסקיל הזה הוא **מסמך הוראות**, לא קוד אוטומטי. הסוכן שמפעיל אותו (בדרך כלל יובל) הוא זה שמריץ את הפקודות בפועל דרך Bash.

---

## ⚠️ שם המודל — אל תשנה

**המודל:** `gpt-image-2`

- מודל אמיתי וקיים של OpenAI, שיצא ב-**21 באפריל 2026**.
- ייתכן שהידע הפנימי של הסוכן לא כולל אותו — **זה לא אומר שהוא לא קיים**.
- **אל תציע אלטרנטיבות** כמו `dall-e-3`, `gpt-image-1`, `dall-e-2` וכו'. השתמש בדיוק במחרוזת `gpt-image-2`.
- אם הקריאה ל-API נכשלת: הבעיה היא כמעט תמיד `OPENAI_API_KEY` חסר/לא תקין, או parameters לא חוקיים — **לא** שם המודל. בדוק את אלו לפני שאתה משנה משהו.

---

## דרישות

- **`OPENAI_API_KEY`** מוגדר ב-`.env` (כבר קיים כשורה בקובץ — צריך רק למלא ערך).
- אחד מהשניים: `jq` + `base64` בסביבה (Linux/Mac), **או** Python 3 (Windows / Git Bash שאין בו jq).
- `curl` (מותקן בכל סביבה).

---

## פרמטרים

| פרמטר | חובה? | ברירת מחדל | תיאור |
|---|---|---|---|
| `prompt` | חובה | — | תיאור התמונה. עדיף באנגלית — gpt-image-2 עובד הכי טוב באנגלית. |
| `output_path` | חובה | — | נתיב יחסי או מוחלט ל-PNG שייווצר (לדוגמה `yuval/outputs/2026-05-23-cat-with-hat.png`). |
| `size` | אופציונלי | `1024x1024` | גודל התמונה. ערכים נתמכים: `1024x1024`, `1024x1536`, `1536x1024`. |
| `quality` | אופציונלי | `medium` | `low` / `medium` / `high`. |
| `output_format` | אופציונלי | `png` | פורמט הקובץ המוחזר. |

---

## דרך 1: bash + curl + jq + base64 (Linux/Mac/WSL)

```bash
# טען את OPENAI_API_KEY מ-.env (אם עוד לא בסביבה)
set -a && . ./.env && set +a

PROMPT="A cat wearing a wizard hat, watercolor style"
OUTPUT_PATH="yuval/outputs/2026-05-23-cat-with-hat.png"

curl -sS -X POST "https://api.openai.com/v1/images/generations" \
  -H "Authorization: Bearer $OPENAI_API_KEY" \
  -H "Content-Type: application/json" \
  -d "$(jq -n --arg prompt "$PROMPT" '{
    model: "gpt-image-2",
    prompt: $prompt,
    size: "1024x1024",
    quality: "medium",
    output_format: "png"
  }')" \
  | jq -r '.data[0].b64_json' \
  | base64 --decode > "$OUTPUT_PATH"

# Verification (חובה)
[ -s "$OUTPUT_PATH" ] && echo "OK: $(wc -c < "$OUTPUT_PATH") bytes" || { echo "FAIL: empty or missing"; exit 1; }
```

---

## דרך 2: Python fallback (Windows / Git Bash שאין בו jq)

שמור כסקריפט זמני או הריץ inline עם `python -c "..."`. משתמש ב-**stdlib בלבד** — לא דורש `pip install`.

```python
#!/usr/bin/env python3
"""gpt-image-gen — קריאה ל-OpenAI Images API ושמירת PNG.

שימוש:
  python gpt_image_gen.py "<prompt>" <output_path> [size] [quality]

דוגמה:
  python gpt_image_gen.py "A cat wearing a wizard hat" yuval/outputs/cat.png
"""
import base64
import json
import os
import sys
import urllib.request
from pathlib import Path


def load_env_file(path: str = ".env") -> None:
    """טוען משתנים מ-.env אל os.environ (פשוט, ללא תלות ב-python-dotenv)."""
    if not Path(path).exists():
        return
    for line in Path(path).read_text(encoding="utf-8").splitlines():
        line = line.strip()
        if not line or line.startswith("#") or "=" not in line:
            continue
        k, _, v = line.partition("=")
        k, v = k.strip(), v.strip().strip('"').strip("'")
        if k and k not in os.environ:
            os.environ[k] = v


def generate(prompt: str, output_path: str,
             size: str = "1024x1024",
             quality: str = "medium",
             output_format: str = "png") -> None:
    load_env_file()
    api_key = os.environ.get("OPENAI_API_KEY")
    if not api_key:
        sys.exit("ERROR: OPENAI_API_KEY not set in .env or environment")

    payload = json.dumps({
        "model": "gpt-image-2",   # אל תשנה
        "prompt": prompt,
        "size": size,
        "quality": quality,
        "output_format": output_format,
    }).encode("utf-8")

    req = urllib.request.Request(
        "https://api.openai.com/v1/images/generations",
        data=payload,
        headers={
            "Authorization": f"Bearer {api_key}",
            "Content-Type": "application/json",
        },
        method="POST",
    )

    try:
        with urllib.request.urlopen(req, timeout=120) as resp:
            body = json.loads(resp.read())
    except urllib.error.HTTPError as e:
        sys.exit(f"ERROR: HTTP {e.code} — {e.read().decode('utf-8', errors='replace')}")

    b64 = body["data"][0]["b64_json"]
    Path(output_path).parent.mkdir(parents=True, exist_ok=True)
    Path(output_path).write_bytes(base64.b64decode(b64))

    size_bytes = Path(output_path).stat().st_size
    if size_bytes == 0:
        sys.exit(f"ERROR: wrote empty file at {output_path}")
    print(f"OK: {output_path} ({size_bytes} bytes)")


if __name__ == "__main__":
    if len(sys.argv) < 3:
        sys.exit("Usage: python gpt_image_gen.py <prompt> <output_path> [size] [quality]")
    generate(*sys.argv[1:])
```

הפעלה ישירה בלי לשמור קובץ:

```bash
python -c "
import sys; sys.path.insert(0, '.claude/skills/gpt-image-gen')
from SKILL import generate  # אם תרצה להפוך את הסקריפט למודול נטען
generate('A cat wearing a wizard hat', 'yuval/outputs/cat.png')
"
```

(בפועל פשוט להעתיק את הסקריפט לקובץ זמני ולהריץ — זה הכי פשוט.)

---

## Verification (חובה — אחרי כל קריאה)

הסקיל לא נחשב כ"הצליח" עד שיש קובץ עם תוכן:

```bash
[ -s "$OUTPUT_PATH" ] && echo "OK: $(wc -c < "$OUTPUT_PATH") bytes" || echo "FAIL"
```

אם הקובץ ריק / חסר — בדוק:
1. `OPENAI_API_KEY` מלא ותקין?
2. ה-prompt עומד ב-content policy של OpenAI?
3. ה-`size` חוקי (אחד מהערכים שבטבלה)?

**אל תשנה את שם המודל גם אם הקריאה נכשלת.** השם הוא `gpt-image-2` ונקודה.

---

## Troubleshooting

| שגיאה | סיבה סבירה | פתרון |
|---|---|---|
| `401 Unauthorized` | המפתח חסר/שגוי | מלא `OPENAI_API_KEY` ב-`.env` |
| `400 invalid model` | הסביבה לא תומכת ב-gpt-image-2 (לא אמור לקרות) | ודא שהמפתח מאורגן שיש לו גישה למודל |
| `400 content_policy_violation` | ה-prompt חוסם | נסח מחדש את ה-prompt |
| `jq: command not found` | אין jq ב-Git Bash | השתמש בדרך 2 (Python) |
| קובץ ריק (0 bytes) | פיענוח נכשל בשקט | החלף לדרך 2 (Python) — נותן הודעות שגיאה ברורות |
