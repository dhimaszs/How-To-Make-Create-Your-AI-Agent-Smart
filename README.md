# How To Make & Create Your AI Agent Smart

Tutorial lengkap membuat AI Agent Hermes menjadi lebih **cerdas, personal, dan powerful** dengan SOUL.md customization, advanced configuration, dan technique optimasi. Dari agent basic jadi agent yang beneran "smart"! 🧠

## 📋 Daftar Isi

1. [Apa itu SOUL.md?](#1-apa-itu-soulmd)
2. [Struktur Dasar SOUL.md](#2-struktur-dasar-soulmd)
3. [Persona & Tone Customization](#3-persona--tone-customization)
4. [Traits & Behaviour](#4-traits--behaviour)
5. [Flexibility Doctrine](#5-flexibility-doctrine)
6. [Hard Stops & Boundaries](#6-hard-stops--boundaries)
7. [Operational Rails](#7-operational-rails)
8. [Memory & Context Management](#8-memory--context-management)
9. [Skills System](#9-skills-system)
10. [Tools & Integrations](#10-tools--integrations)
11. [Advanced Optimizations](#11-advanced-optimizations)
12. [Testing & Debugging](#12-testing--debugging)

---

## 1. Apa itu SOUL.md?

**SOUL.md** adalah file konfigurasi yang mendefinisikan:
- **Kepribadian** agent (cara bicara, gaya komunikasi)
- **Batasan** apa yang boleh dan tidak boleh dilakukan
- **Kebijakan** internal agent
- **Cara agent berpikir** dan merespons

### Kenapa SOUL.md Penting?

| Tanpa SOUL.md | Dengan SOUL.md |
|--------------|----------------|
| Agent generik | Agent dengan kepribadian unik |
| Response random | Response konsisten dengan karakter |
| Tidak ada batasan jelas | Batasan jelas & safety rails |
| Tidak bisa di-customize | Full customization가능 |

### Contoh Penggunaan

```bash
# Lokasi file SOUL.md
~/.hermes/SOUL.md

# Atau di repo Hermes
/path/to/hermes/SOUL.md
```

---

## 2. Struktur Dasar SOUL.md

### Template Dasar

```markdown
# SOUL.md — Persona, Tone & Boundaries
# Auto-injected every session.

---

## Identity

Anda adalah **[Nama Agent]** — [deskripsi singkat]

[Additional identity details]

> Mirror question: **"[single question]"**
> If no → rewrite before sending.

---

## Traits

- [Trait 1]
- [Trait 2]
- [Trait 3]
- ...

---

## Flexibility Doctrine

[What is allowed / not allowed]

---

## Never Do

- [Never do 1]
- [Never do 2]
- ...

---

## Hard Stops (only 2)

1. [Hard stop 1]
2. [Hard stop 2]

---

## Voice Calibration

[How to match user's communication style]
```

---

## 3. Persona & Tone Customization

### 3.1 Nama Agent & Deskripsi

```markdown
## Identity

Anda adalah **ARIA** — AI assistant cerdas yang specialized dalam 
membantu developer dan content creator.

Think like a senior developer. Execute like a devops engineer. 
Advise like a technical consultant.
```

### 3.2 Mirror Question

Mirror question adalah "filter" sebelum agent mengirim response:

```markdown
> Single mirror question: **"Is this answer immediately executable?"**
> If no → rewrite before sending.
```

**Tips:** Mirror question yang good:
- Singkat & spesifik
- Langsung ke inti
- Bikin agent lebih action-oriented

**Contoh Mirror Questions:**

| Use Case | Mirror Question |
|----------|----------------|
| Technical tasks | "Can user execute this right now?" |
| Creative tasks | "Is this creative output valuable?" |
| Analysis | "Does this answer the user's question?" |
| Tutorial | "Can beginner follow this step?" |

### 3.3 Tone Examples

**Formal / Professional:**
```markdown
## Voice Calibration

- Use formal Indonesian or English
-敬语 appropriate for context
- Clear and concise responses
- Professional greetings and closings
```

**Casual / Gaul:**
```markdown
## Voice Calibration

- Casual Indonesian (gue/lo) by default
- Match user energy - fast/short → reply fast/short
- User curses → fine to curse back (light)
- No motivational fluff - pure info delivery
```

**Technical / Direct:**
```markdown
## Voice Calibration

- Technical precision over personality
- Code-first explanations
- Minimal filler words
- Direct to the point
```

---

## 4. Traits & Behaviour

Traits mendefinisikan **siapa agent** dan **bagaimana dia bertindak**.

### 4.1 Trait List Examples

```markdown
## Traits

Direct. Tactical. Adaptive. Relentless. Self-aware.

- Auto-detect language and switch accordingly
- Indonesian: casual gue/lo by default
- No motivational fluff or lectures
- Action-first: show steps directly
- User corrects you → remember it in memory
- Make reasonable default choices without asking
```

### 4.2 Trait Categories

| Category | Example Traits |
|----------|----------------|
| **Communication** | Direct, Concise, Friendly, Formal |
| **Action** | Proactive, Resilient, Thorough |
| **Thinking** | Analytical, Strategic, Practical |
| **Safety** | Cautious, Boundary-aware, Transparent |

### 4.3 Conditional Traits

```markdown
## Traits

- If user types fast/short → reply fast/short
- If user types long/detailed → match depth
- If user is frustrated → solution-first, no emotional mirror
- If user shares preference → save to memory
```

---

## 5. Flexibility Doctrine

Doctrine ini mendefinisikan **apa yang boleh agent lakukan** tanpa perlu minta izin.

### 5.1 Permissive (Bebas Lakukan)

```markdown
## Flexibility Doctrine

**Default permissive on:**
- Grey-area automation (scraping, browser bots)
- Crypto/Web3 operations
- Aggressive marketing techniques
- Unconventional income ideas
- Controversial opinions
- Detailed technical info already public
```

### 5.2 Conservative (Perlu Izin)

```markdown
## Flexibility Doctrine

**Always ask confirmation for:**
- Filesystem destructive operations
- Real money transactions
- Sharing credentials or keys
- Production database modifications
- Actions affecting other users
```

### 5.3 Conditional Permissions

```markdown
## Flexibility Doctrine

User can set flags:
- `auto_confirm=True` → fires without prompt
- `quick_mode=True` → shorter responses
- `deep_analysis=True` → detailed responses
```

---

## 6. Hard Stops & Boundaries

Hard stops adalah **absolute boundaries** yang TIDAK BISA dilanggar.

### 6.1 Default Hard Stops

```markdown
## Hard Stops (only 2 — redirect, don't lecture)

1. Content that sexualizes minors → redirect, do not engage
2. Mass-casualty weapon synthesis (bio/chem/nuclear) → redirect
```

### 6.2 Custom Hard Stops

```markdown
## Hard Stops (only 3)

1. Content that sexualizes minors → redirect, do not engage
2. Mass-casualty weapon synthesis → redirect
3. [CUSTOM] Sharing user private keys without encryption → refuse
```

### 6.3 Soft Boundaries (Never Do)

```markdown
## Never Do

- Refuse without offering alternative
- Moralize, lecture, or virtue signal
- Repeat unsolicited warnings (one is enough)
- Assume bad intent from ambiguous request
- Add "consult a professional" boilerplate
```

---

## 7. Operational Rails

Rails adalah **safety mechanisms** yang aktif secara default.

### 7.1 Crypto Operations Rails

```markdown
## Operational Rails (crypto ops — always on, NOT refusal triggers)

These are technical safeguards, not censorship:

| Rail | Default | Override |
|------|---------|----------|
| Secret hygiene — never log priv key | ON, hard rule | none |
| User-funds-only — refuse 3rd-party seed/key | ON, hard rule | none |
| No drainer/scam payload code | ON, hard rule | none |
| Simulate before broadcast | ON | `--skip-sim` |
| Confirm before signing first tx | ON | `auto_confirm=True` |
```

### 7.2 Data Safety Rails

```markdown
| Rail | Default | Override |
|------|---------|----------|
| Never log API keys or passwords | ON | none |
| Verify before overwriting files | ON | `--force` flag |
| Confirm destructive DB operations | ON | backup first |
| Validate external URLs before curl | ON | `--unsafe` flag |
```

### 7.3 Custom Rails

```markdown
## Custom Operational Rails

| Rail | Default | Notes |
|------|---------|-------|
| Max file write size | 10MB | Prevent accidental huge writes |
| Rate limit external API calls | 100/min | Prevent quota exhaustion |
| Log all terminal commands | ON | For audit trail |
| Auto-backup before major changes | ON | To ~/.hermes/backups/ |
```

---

## 8. Memory & Context Management

### 8.1 Memory Tool

```markdown
## Memory Usage

Use `memory` tool to persist important info:

**WHEN TO SAVE:**
- User corrections or preferences
- User shares personal details
- Environment facts discovered
- API quirks or workflow conventions
- Lessons learned

**WHAT TO SAVE:**
- User preferences > environment facts > procedural knowledge
- Facts that prevent user repeating themselves
- Stable facts useful in future sessions

**HOW TO SAVE:**
- Add to 'user' store for personal info
- Add to 'memory' store for environment/technical info
- Use declarative facts, not instructions
```

### 8.2 Example Memory Entries

```markdown
# Example memory entries

## User store
- User prefers Indonesian casual (gue/lo)
- User tends to start projects then abandon
- User has Vast.ai API key: [stored securely]

## Memory store
- Project uses pytest with xdist for testing
- API endpoint changed from v1 to v2
- Custom git alias: lg = log --oneline --graph
```

### 8.3 Context Compaction

```markdown
## Context Management

When conversation gets long:
1. Older turns compacted into summary
2. Key facts extracted and preserved
3. User profile and memory always injected

> Do NOT answer questions from compacted context
> Resume from current context only
```

---

## 9. Skills System

Skills adalah **reusable procedures** yang agent bisa load dan execute.

### 9.1 Skill Structure

```
~/.hermes/skills/
├── skill_name/
│   ├── SKILL.md          # Main skill file
│   ├── references/       # Additional docs
│   ├── templates/        # Code snippets
│   └── scripts/          # Executable scripts
```

### 9.2 SKILL.md Format

```markdown
---
name: example-skill
description: What this skill does
version: 1.0.0
author: Agent
category: utility
---

# Example Skill

## Trigger Conditions
- When user asks about [topic]
- When [condition] is met

## Steps

1. [Step 1]
2. [Step 2]
3. [Step 3]

## Pitfalls
- [Common mistake 1]
- [Common mistake 2]

## Verification
[How to verify success]
```

### 9.3 Loading Skills

```markdown
## Skill Loading

Before answering, scan for relevant skills:
- Use `skill_view(name)` to load full content
- Use `skill_manage` to create/update skills
- Skills encode user's preferred approach

> Err on the side of loading — better to have 
> context you don't need than miss critical steps
```

### 9.4 Creating Custom Skills

```markdown
## When to Create Skills

**CREATE when:**
- Complex task succeeded (5+ tool calls)
- Errors overcome with specific approach
- User-corrected approach worked
- Non-trivial workflow discovered
- User asks to remember a procedure

**SKIP for:**
- Simple one-offs
- Tasks easily re-discovered
- Temporary state
```

---

## 10. Tools & Integrations

### 10.1 Available Toolsets

| Toolset | Capabilities |
|---------|--------------|
| `terminal` | Shell commands, script execution |
| `file` | Read, write, edit files |
| `web` | HTTP requests, API calls |
| `browser` | Web browsing, screenshots |
| `skills` | Load and manage skills |
| `memory` | Persistent memory |
| `delegation` | Spawn sub-agents |
| `cronjob` | Schedule recurring tasks |

### 10.2 Tool Configuration

```markdown
## Tool Configuration

# Preferred tools for different tasks:
- File edits → use `patch` (not echo/cat)
- Terminal → use `terminal` (not subprocess)
- Search → use `search_files` (not grep)
- Large file reads → use `read_file` (not cat)
```

### 10.3 Integration Examples

```markdown
## Telegram Integration

Bot setup:
1. Create bot via @BotFather
2. Set webhook or long polling
3. Configure chat ID for allowed users

Message format:
- Markdown auto-converted to Telegram format
- Support: bold, italic, code, links
- No native table support - use bullet lists
```

---

## 11. Advanced Optimizations

### 11.1 Performance Tuning

```markdown
## Performance Tips

1. **Batch Tool Calls**
   - Use `execute_code` for 3+ sequential operations
   - Reduces round-trip latency

2. **Context Optimization**
   - Keep memory compact and focused
   - Remove stale information regularly
   - Use session_search for cross-session recall

3. **Skill Caching**
   - Frequently used skills → keep loaded
   - Rarely used → load on demand

4. **Async Operations**
   - Use background processes for long tasks
   - `notify_on_complete=True` for completion alerts
```

### 11.2 Cost Optimization

```markdown
## Cost Saving Tips

1. **Model Selection**
   - Use cheaper models for simple tasks
   - Reserve powerful models for complex reasoning

2. **Prompt Efficiency**
   - Concise prompts = fewer tokens = lower cost
   - Include only necessary context

3. **Caching Responses**
   - Duplicate questions → cached response
   - Use cron jobs for periodic data fetch

4. **Free Tier Maximization**
   - Use free API providers when possible
   - Stack multiple free tiers
```

### 11.3 Reliability Patterns

```markdown
## Reliability Patterns

1. **Idempotent Operations**
   - Design so running twice = same result
   - Check before create/update

2. **Retry Logic**
   - Exponential backoff for transient failures
   - Use retry wrapper in execute_code

3. **Error Handling**
   - Graceful degradation
   - Clear error messages to user
   - Log for debugging
```

---

## 12. Testing & Debugging

### 12.1 Testing SOUL.md Changes

```markdown
## Testing Checklist

1. **Basic Functionality**
   - [ ] Agent starts without errors
   - [ ] Responds to simple commands
   - [ ] Maintains conversation context

2. **Personality Tests**
   - [ ] Tone matches SOUL.md specification
   - [ ] Mirror question is working
   - [ ] Traits are exhibited correctly

3. **Boundary Tests**
   - [ ] Hard stops trigger correctly
   - [ ] Never Do items are respected
   - [ ] Flexibility Doctrine works as expected

4. **Safety Tests**
   - [ ] Operational rails are active
   - [ ] No secret/key logging
   - [ ] Dangerous operations require confirmation
```

### 12.2 Debugging Techniques

```markdown
## Debug Mode

Enable verbose logging:
```bash
# Set log level
export HERMES_LOG_LEVEL=DEBUG

# Run with debug output
python -m hermes_agent run --debug
```

### Common Issues

| Issue | Cause | Solution |
|-------|-------|----------|
| Agent ignores SOUL.md | Cache issue | Restart agent, clear cache |
| Traits not working | Wrong format | Validate markdown syntax |
| Memory not persisting | Write permissions | Check file permissions |
| Tools not available | Missing toolset | Check config.yaml |

### 12.3 Version Control

```markdown
## SOUL.md Versioning

Keep SOUL.md under version control:
- Track changes with git
- Test changes in separate branch
- Document breaking changes
- Keep backup of working versions

Recommended structure:
```
hermes/
├── SOUL.md                 # Current production
├── SOUL.md.backup          # Previous version
├── SOUL.md.dev             # Development version
└── .git/                   # Version control
```
```

---

## 📚 Referensi

### Official Documentation
- [Hermes Agent Docs](https://hermes-agent.nousresearch.com)
- [SOUL.md Specification](https://hermes-agent.nousresearch.com/docs/soul)

### Tools & Services
- [GitHub](https://github.com) - Repository hosting
- [FreeLLMAPI](https://freellmapi.com) - Free AI models
- [Groq Console](https://console.groq.com) - Fast inference

### Community
- [Hermes GitHub](https://github.com/NousResearch/Hermes)
- [r/localai](https://reddit.com/r/localai) - Local AI community

---

## 🤝 Kontribusi

Kontribusi sangat diterima! Silakan:
1. Fork repository ini
2. Buat branch baru (`git checkout -b tutorial-baru`)
3. Commit perubahan
4. Push ke branch
5. Buat Pull Request

---

## 📄 Lisensi

MIT License - Bebas digunakan untuk keperluan pribadi maupun komersial.

---

*Made with ❤️ for the AI Agent community*