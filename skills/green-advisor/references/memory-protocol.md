# green-advisor — протокол памяти

Читается ПОСЛЕ выдачи совета, когда решается, что сохранить. В горячем пути анализа не нужен.

### File Format

Canonical path: `{MEMORY_DIR}/Профили/green-advisor.md` (always absolute with `~/`).

```yaml
---
# === User Profile ===
role: "Founder / CTO / Manager / etc."
domain: "Tech / Finance / etc."
career_stage: "early / mid / senior / transition"
mastery_path: "описание текущего пути к мастерству"

# === Key Players (persistent map, max 15 entries) ===
players:
  - name: "Инициалы или код"
    relationship: "boss / peer / report / partner / rival"
    archetype: "[AoS:Charmer] / [LHN:L10] / etc."
    patterns: "краткое описание паттернов поведения"
    last_updated: "YYYY-MM-DD"

# === Active Strategies (max 5, archive completed) ===
active_strategies:
  - situation: "краткое описание"
    principles: ["[48LP:L3]", "[33SW:S23]"]
    action: "что делаем"
    status: "planned / executing / monitoring / completed / abandoned"
    started: "YYYY-MM-DD"

# === Lessons Learned (max 20, FIFO oldest) ===
lessons:
  - date: "YYYY-MM-DD"
    situation: "краткое"
    principle_applied: "[48LP:L1]"
    outcome: "сработало / не сработало / частично"
    insight: "что узнали"

updated: "YYYY-MM-DD"
---

## Session Log

### YYYY-MM-DD: Тема
- Ситуация: ...
- Рекомендации: [48LP:LX], [LHN:LY]
- Решение: ...
- Follow-up: ...
```

### Sizing Guidelines

- YAML frontmatter: < 3KB
- Total file: < 8KB
- Section caps enforce bounded growth (see below)

### Memory Update (post-advisory)

After delivering advice and the user has responded, evaluate what to persist.
This is NOT a numbered advisory step — it runs silently after the 4-step Greene Analysis.

**Read-before-write**: ALWAYS re-read `{MEMORY_DIR}/Профили/green-advisor.md` immediately
before writing. Never write based on the copy loaded at session start — it may be stale
if another session updated it.

**Always update:**
- New key players mentioned → add to `players` with observed archetype (use initials/codes, not full names)
- New strategy recommended → add to `active_strategies` with status "planned"
- Outcome reported for past strategy → update status, add to `lessons`
- Session log entry → append to `## Session Log`

**Update on user confirmation:**
- Changes to `role`, `domain`, `career_stage`, `mastery_path`
- Archetype changes for existing players (if the user reveals new information)

**Never overwrite, always append:**
- `lessons` — only append, never delete (learning history)
- `## Session Log` — only append, chronological
- `players` — update existing entries, never remove (people may reappear)

**Overwrite allowed:**
- `active_strategies` status changes
- Player `patterns` and `archetype` (on new evidence)
- Top-level profile fields (`role`, `domain`, etc.)

### Section Caps

- `players`: max 15 entries. При превышении — архивировать давно неактивных (last_updated > 6 мес.) в `## Archived Players`
- `active_strategies`: max 5. Completed/abandoned → переносить в `lessons`
- `lessons`: max 20. При превышении — удалять самые старые (FIFO)
- `## Session Log`: max 30 entries. При превышении — суммаризировать самые старые в `## Archived Insights` (user-confirmed)

### Compaction

When `## Session Log` exceeds 30 entries, summarize the oldest entries into `## Archived Insights` (user-confirmed before compaction). Archived format: `"[DATE] [TAG] outcome — insight"` (one line per entry). Preserve: player codes, principle tags, outcome keywords.

### Write Failure Handling

- If YAML serialization fails → log warning, do NOT write corrupted data
- If file write fails → inform user, suggest manual save

### Privacy Controls

**Data lifecycle:**
- Use initials or codes for player names, not full names
- On first use, show notice: "Memory file stores personal context at {MEMORY_DIR}/Профили/green-advisor.md"
- User can delete file at any time to reset memory

**Git protection:**
- The memory file is private: keep `{MEMORY_DIR}` out of any public repository.
