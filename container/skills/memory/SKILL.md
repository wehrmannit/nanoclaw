---
name: memory
description: Store and recall personal facts about the user — addresses, preferences, contacts, schedules, and any other information they share. Uses MemOS for semantic search and memory evolution when available, falls back to local JSON storage. Use proactively whenever the user mentions factual information worth remembering, and recall facts when they might be relevant.
allowed-tools: Bash(memory-cli:*), Bash(memos-cli:*)
---

# Personal Memory

Store and recall facts the user shares with you. This is your long-term memory for personal information.

## Which tool to use

- **memos-cli** — Semantic memory (MemOS). Use when available (`memos-cli status` returns healthy). Supports fuzzy/semantic search, auto-deduplication, and memory evolution.
- **memory-cli** — Local JSON fallback. Always available. Simple keyword search.

Check MemOS first: `memos-cli status`. If it fails, use `memory-cli` instead.

## When to store

**Proactively store** whenever the user mentions:
- Addresses (home, work, doctor, gym, etc.)
- People and contacts (names, roles, phone numbers)
- Preferences (food, travel, routines)
- Schedules and recurring events
- Medical info (doctor names, conditions, medications)
- Work info (office location, colleagues, projects)
- Any factual detail they'd expect you to remember

You don't need to ask permission — just store it and confirm briefly.

## When to recall

**Proactively check** stored facts when:
- The user asks to go somewhere (check stored addresses)
- The user mentions a person (check contacts)
- The user asks "do you remember..." or "what was..."
- Planning or scheduling (check stored schedules/preferences)
- Any context where a stored fact could be helpful

Always search memory before saying "I don't know" about something the user may have told you before.

## MemOS commands (preferred)

```bash
memos-cli status                                 # Check if MemOS is available
memos-cli add "Therapist Dr. Mueller at Mariahilfer Str. 42, 1070 Vienna"
memos-cli search "therapist address"             # Semantic search
memos-cli chat "Where is my therapist?"          # Chat with memory context
memos-cli list                                   # List all memories
memos-cli feedback "Therapist moved to Neubaugasse 15"  # Correct memories
memos-cli delete <memory_id>                     # Remove a memory
```

## Local fallback commands

```bash
memory-cli store address "Therapist at Mariahilfer Str. 42"
memory-cli search therapist
memory-cli list [category]
memory-cli delete <id>
```

Categories: `personal`, `address`, `preference`, `contact`, `medical`, `work`, `schedule`, `other`
