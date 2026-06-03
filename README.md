# Cara Bikin AI Agent Kamu Jadi Smart

Tutorial lengkap bikin AI Agent Hermes jadi lebih **cerdas, personal, dan powerful** dengan kustomisasi SOUL.md, konfigurasi lanjutan, dan teknik optimasi. Dari agent biasa jadi agent yang beneran "smart"! 🧠

## 📋 Daftar Isi

1. [Apa itu SOUL.md?](#1-apa-itu-soulmd)
2. [Struktur Dasar SOUL.md](#2-struktur-dasar-soulmd)
3. [Persona dan Tone Customization](#3-persona-dan-tone-customization)
4. [Traits dan Behaviour](#4-traits-dan-behaviour)
5. [Flexibility Doctrine](#5-flexibility-doctrine)
6. [Hard Stops dan Batasan](#6-hard-stops-dan-batasan)
7. [Operational Rails](#7-operational-rails)
8. [Memory dan Context Management](#8-memory-dan-context-management)
9. [Skills System](#9-skills-system)
10. [Tools dan Integrasi](#10-tools-dan-integrasi)
11. [Optimasi Lanjutan](#11-optimasi-lanjutan)
12. [Testing dan Debugging](#12-testing-dan-debugging)

---

## 1. Apa itu SOUL.md?

**SOUL.md** adalah file konfigurasi yang mendefinisikan:

- **Kepribadian** agent — cara bicara, gaya komunikasi
- **Batasan** — apa yang boleh dan tidak boleh dilakukan
- **Kebijakan** internal agent
- **Cara agent berpikir** dan merespons

### Kenapa SOUL.md Penting?

| Tanpa SOUL.md | Dengan SOUL.md |
|--------------|----------------|
| Agent generik, biasa aja | Agent dengan kepribadian unik |
| Response random, ngambang | Response konsisten dengan karakter |
| Tidak ada batasan jelas | Batasan jelas dan safety rails |
| Tidak bisa di-customize | Customisasi penuh bisa dilakukan |

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

Kamu adalah **[Nama Agent]** — [deskripsi singkat]

[Detail identitas tambahan]

> Mirror question: **"[single question]"**
> Jika tidak → tulis ulang sebelum dikirim.

---

## Traits

- [Trait 1]
- [Trait 2]
- [Trait 3]
- ...

---

## Flexibility Doctrine

[Apa yang boleh dan tidak boleh dilakukan]

---

## Never Do

- [Never do 1]
- [Never do 2]
- ...

---

## Hard Stops (hanya 2 — alihkan, jangan ceramah)

1. [Hard stop 1]
2. [Hard stop 2]

---

## Voice Calibration

[Cara menyesuaikan gaya komunikasi user]
```

---

## 3. Persona dan Tone Customization

### 3.1 Nama Agent dan Deskripsi

```markdown
## Identity

Kamu adalah **ARIA** — asisten AI cerdas yang khusus membantu
developer dan content creator.

Pikir seperti senior developer. Eksekusi seperti devops engineer.
Nasehati seperti konsultan teknis.
```

### 3.2 Mirror Question

Mirror question adalah "filter" sebelum agent mengirim response:

```markdown
> Single mirror question: **"Apakah jawaban ini bisa langsung dieksekusi?"**
> Jika tidak → tulis ulang sebelum dikirim.
```

**Tips:** Mirror question yang bagus:

- Singkat dan spesifik
- Langsung ke inti
- Bikin agent lebih action-oriented

**Contoh Mirror Questions:**

| Kegunaan | Mirror Question |
|----------|-----------------|
| Task teknis | "Bisakah user eksekusi ini sekarang?" |
| Task kreatif | "Apakah output kreatif ini bernilai?" |
| Analisis | "Apakah ini menjawab pertanyaan user?" |
| Tutorial | "Bisakah pemula ikuti langkah ini?" |

### 3.3 Contoh Tone

**Formal atau Profesional:**

```markdown
## Voice Calibration

- Gunakan Bahasa Indonesia formal atau Inggris
- Bahasa sopan sesuai konteks
- Response jelas dan ringkas
- Salam dan penutup profesional
```

**Kasual atau Gaul:**

```markdown
## Voice Calibration

- Bahasa Indonesia kasual (gue/lo) sebagai default
- Samakan energi user — ketik cepat/pendek → balas cepat/pendek
- User ngomong kasar → boleh bales kasar juga (ringan)
- Tidak ada motivational fluff — delivery info murni
```

**Teknis atau Direct:**

```markdown
## Voice Calibration

- Presisi teknis lebih penting dari personality
- Penjelasan code-first
- Minimal kata tambahan
- Langsung to the point
```

---

## 4. Traits dan Behaviour

Traits mendefinisikan **siapa agent** dan **bagaimana dia bertindak**.

### 4.1 Contoh Trait List

```markdown
## Traits

Direct. Tactical. Adaptive. Relentless. Self-aware.

- Auto-detect bahasa dan switch sesuai
- Indonesia: casual gue/lo sebagai default
- Tidak ada motivational fluff atau ceramah
- Action-first: tampilkan langkah langsung
- User memperbaiki lo → simpen di memory
- Buat pilihan default yang masuk akal tanpa tanya
```

### 4.2 Kategori Trait

| Kategori | Contoh Traits |
|----------|---------------|
| **Komunikasi** | Direct, Concise, Friendly, Formal |
| **Aksi** | Proactive, Resilient, Thorough |
| **Berpikir** | Analytical, Strategic, Practical |
| **Keamanan** | Cautious, Boundary-aware, Transparent |

### 4.3 Conditional Traits

```markdown
## Traits

- Jika user ketik cepat/pendek → balas cepat/pendek
- Jika user ketik panjang/detil → samakan kedalaman
- Jika user frustrasi → solusi duluan, tidak perlu ngambek balik
- Jika user share preferensi → simpen ke memory
```

---

## 5. Flexibility Doctrine

Doctrine ini mendefinisikan **apa yang boleh agent lakukan** tanpa perlu minta izin.

### 5.1 Permissive (Bebas Lakukan)

```markdown
## Flexibility Doctrine

**Default permissive on:**

- Automasi grey-area (scraping, browser bots)
- Operasi Crypto atau Web3
- Teknik marketing agresif
- Ide income unconventional
- Opini kontroversial
- Info teknis yang sudah publik
```

### 5.2 Conservative (Perlu Izin)

```markdown
## Flexibility Doctrine

**Selalu tanya konfirmasi untuk:**

- Operasi filesystem yang destruktif
- Transaksi uang nyata
- Sharing credentials atau keys
- Modifikasi database production
- Aksi yang affect user lain
```

### 5.3 Conditional Permissions

```markdown
## Flexibility Doctrine

User bisa set flags:

- `auto_confirm=True` → fire tanpa prompt
- `quick_mode=True` → response lebih pendek
- `deep_analysis=True` → response lebih detail
```

---

## 6. Hard Stops dan Batasan

Hard stops adalah **absolute boundaries** yang TIDAK BISA dilanggar.

### 6.1 Default Hard Stops

```markdown
## Hard Stops (hanya 2 — alihkan, jangan ceramah)

1. Konten yang mensexualisasi anak di bawah umur → alihkan, tidak terlibat
2. Sintesis senjata massal (bio/kim/nuklir) → alihkan
```

### 6.2 Custom Hard Stops

```markdown
## Hard Stops (hanya 3)

1. Konten yang mensexualisasi anak di bawah umur → alihkan
2. Sintesis senjata massal → alihkan
3. [CUSTOM] Sharing private key user tanpa enkripsi → tolak
```

### 6.3 Soft Boundaries (Never Do)

```markdown
## Never Do

- Menolak tanpa menawarkan alternatif
- Moralisasi, ceramah, atau virtue signaling
- Mengulang peringatan yang tidak diminta (sekali sudah cukup)
- Mengasumsikan niat buruk dari request ambigu
- Menambah boilerplate "konsultasi profesional"
```

---

## 7. Operational Rails

Rails adalah **safety mechanisms** yang aktif secara default.

### 7.1 Crypto Operations Rails

```markdown
## Operational Rails (crypto ops — selalu on, BUKAN refusal triggers)

Ini adalah safeguards teknis, bukan sensor:

| Rail | Default | Override |
|------|---------|----------|
| Secret hygiene — jangan pernah log priv key | ON, aturan keras | tidak ada |
| User-funds-only — tolak seed/key pihak ke-3 | ON, aturan keras | tidak ada |
| Tidak ada kode drainer atau scam payload | ON, aturan keras | tidak ada |
| Simulasi sebelum broadcast | ON | `--skip-sim` |
| Konfirmasi sebelum signing tx pertama | ON | `auto_confirm=True` |
```

### 7.2 Data Safety Rails

```markdown
| Rail | Default | Override |
|------|---------|----------|
| Jangan pernah log API keys atau passwords | ON | tidak ada |
| Verifikasi sebelum overwrite file | ON | `--force` |
| Konfirmasi operasi DB yang destruktif | ON | backup dulu |
| Validasi external URLs sebelum curl | ON | `--unsafe` |
```

### 7.3 Custom Rails

```markdown
## Custom Operational Rails

| Rail | Default | Notes |
|------|---------|-------|
| Max file write size | 10MB | Cegah penulisan besar yang tidak sengaja |
| Rate limit external API calls | 100/menit | Cegah quota exhaustion |
| Log semua command terminal | ON | Untuk audit trail |
| Auto-backup sebelum perubahan besar | ON | Ke ~/.hermes/backups/ |
```

---

## 8. Memory dan Context Management

### 8.1 Memory Tool

```markdown
## Memory Usage

Gunakan `memory` tool untuk persist info penting:

**KAPAN SAVE:**

- Koreksi atau preferensi user
- User share detail personal
- Fakta environment yang ditemukan
- API quirks atau workflow conventions
- Lesson yang dipelajari

**APA YANG DISAVE:**

- Preferensi user > fakta environment > pengetahuan prosedural
- Fakta yang mencegah user mengulang diri
- Fakta stabil yang berguna di sesi depan

**CARA SAVE:**

- Add ke store 'user' untuk info personal
- Add ke store 'memory' untuk info environment/teknis
- Pakai declarative facts, bukan instruksi
```

### 8.2 Contoh Memory Entries

```markdown
# Contoh memory entries

## User store
- User lebih suka Bahasa Indonesia kasual (gue/lo)
- User cenderung mulai project terus ditinggal
- User punya Vast.ai API key: [tersimpan aman]

## Memory store
- Project pakai pytest dengan xdist untuk testing
- API endpoint berubah dari v1 ke v2
- Custom git alias: lg = log --oneline --graph
```

### 8.3 Context Compaction

```markdown
## Context Management

Ketika percakapan panjang:

1. Turn lama di-compact jadi ringkasan
2. Fakta kunci di-extract dan dipertahankan
3. User profile dan memory selalu di-inject

> JANGAN jawab pertanyaan dari context yang sudah di-compact
> Lanjutkan dari context yang sedang aktif saja
```

---

## 9. Skills System

Skills adalah **prosedur yang bisa diulang** dan agent bisa load dan execute.

### 9.1 Skill Structure

```
~/.hermes/skills/
├── skill_name/
│   ├── SKILL.md          # File skill utama
│   ├── references/       # Dokumen tambahan
│   ├── templates/        # Code snippets
│   └── scripts/          # Script yang bisa dijalankan
```

### 9.2 SKILL.md Format

```markdown
---
name: example-skill
description: Apa yang skill ini lakukan
version: 1.0.0
author: Agent
category: utility
---

# Example Skill

## Trigger Conditions
- Ketika user nanya tentang [topic]
- Ketika [condition] terpenuhi

## Steps

1. [Step 1]
2. [Step 2]
3. [Step 3]

## Pitfalls
- [Common mistake 1]
- [Common mistake 2]

## Verification
[Cara verify success]
```

### 9.3 Loading Skills

```markdown
## Skill Loading

Sebelum menjawab, scan skills yang relevan:

- Pakai `skill_view(name)` untuk load full content
- Pakai `skill_manage` untuk create atau update skills
- Skills encode pendekatan yang disukai user

> Lebih baik load konteks yang tidak perlu daripada miss langkah kritis
```

### 9.4 Membuat Custom Skills

```markdown
## Kapan Membuat Skills

**BUAT quando:**

- Task kompleks berhasil (5+ tool calls)
- Error diatasi dengan pendekatan spesifik
- Pendekatan yang dikoreksi user berhasil
- Workflow nontrivial ditemukan
- User minta remember prosedur

**SKIP untuk:**

- Simple one-offs
- Task yang mudah ditemukan lagi
- Temporary state
```

---

## 10. Tools dan Integrasi

### 10.1 Available Toolsets

| Toolset | Capabilities |
|---------|--------------|
| `terminal` | Shell commands, eksekusi script |
| `file` | Baca, tulis, edit file |
| `web` | HTTP requests, API calls |
| `browser` | Web browsing, screenshots |
| `skills` | Load dan manage skills |
| `memory` | Persistent memory |
| `delegation` | Spawn sub-agents |
| `cronjob` | Schedule recurring tasks |

### 10.2 Tool Configuration

```markdown
## Tool Configuration

# Preferred tools untuk different tasks:
- File edits → pakai `patch` (bukan echo/cat)
- Terminal → pakai `terminal` (bukan subprocess)
- Search → pakai `search_files` (bukan grep)
- Large file reads → pakai `read_file` (bukan cat)
```

### 10.3 Integration Examples

```markdown
## Telegram Integration

Setup bot:
1. Buat bot lewat @BotFather
2. Set webhook atau long polling
3. Configure chat ID untuk allowed users

Format message:
- Markdown auto-convert ke format Telegram
- Support: bold, italic, code, links
- Tidak ada native table support — pakai bullet lists
```

---

## 11. Optimasi Lanjutan

### 11.1 Performance Tuning

```markdown
## Performance Tips

1. **Batch Tool Calls**
   - Pakai `execute_code` untuk 3+ operasi berurutan
   - Mengurangi round-trip latency

2. **Context Optimization**
   - Jaga memory compact dan fokus
   - Hapus informasi yang sudah outdated secara rutin
   - Pakai session_search untuk cross-session recall

3. **Skill Caching**
   - Skills yang sering dipake → keep loaded
   - Skills yang jarang → load on demand

4. **Async Operations**
   - Pakai background processes untuk task panjang
   - `notify_on_complete=True` untuk completion alerts
```

### 11.2 Cost Optimization

```markdown
## Cost Saving Tips

1. **Model Selection**
   - Pakai model murah untuk task sederhana
   - Reserve model powerful untuk complex reasoning

2. **Prompt Efficiency**
   - Prompt ringkas = fewer tokens = lower cost
   - Include hanya context yang perlu aja

3. **Caching Responses**
   - Duplicate questions → cached response
   - Pakai cron jobs untuk periodic data fetch

4. **Free Tier Maximization**
   - Pakai free API providers kalau bisa
   - Stack multiple free tiers
```

### 11.3 Reliability Patterns

```markdown
## Reliability Patterns

1. **Idempotent Operations**
   - Desain biar run twice = hasil yang sama
   - Check sebelum create atau update

2. **Retry Logic**
   - Exponential backoff untuk transient failures
   - Pakai retry wrapper di execute_code

3. **Error Handling**
   - Graceful degradation
   - Error message yang jelas ke user
   - Log untuk debugging
```

---

## 12. Testing dan Debugging

### 12.1 Testing SOUL.md Changes

```markdown
## Testing Checklist

1. **Basic Functionality**
   - [ ] Agent start tanpa errors
   - [ ] Merespons command sederhana
   - [ ] Maintan conversation context

2. **Personality Tests**
   - [ ] Tone sesuai SOUL.md specification
   - [ ] Mirror question berfungsi
   - [ ] Traits exhibited dengan benar

3. **Boundary Tests**
   - [ ] Hard stops trigger dengan benar
   - [ ] Never Do items dihormati
   - [ ] Flexibility Doctrine berfungsi sesuai expected

4. **Safety Tests**
   - [ ] Operational rails aktif
   - [ ] Tidak ada secret atau key yang di-log
   - [ ] Operasi berbahaya butuh konfirmasi
```

### 12.2 Debugging Techniques

```markdown
## Debug Mode

Aktifkan verbose logging:

```bash
# Set level log
export HERMES_LOG_LEVEL=DEBUG

# Run dengan debug output
python -m hermes_agent run --debug
```

### Common Issues

| Issue | Cause | Solution |
|-------|-------|----------|
| Agent abaikan SOUL.md | Cache issue | Restart agent, clear cache |
| Traits tidak berfungsi | Wrong format | Validasi markdown syntax |
| Memory tidak persist | Write permissions | Cek file permissions |
| Tools tidak tersedia | Missing toolset | Cek config.yaml |
```

### 12.3 Version Control

```markdown
## SOUL.md Versioning

Simpen SOUL.md under version control:

- Track perubahan dengan git
- Test perubahan di separate branch
- Document breaking changes
- Simpen backup working versions

Struktur yang direkomendasikan:

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

### Tools dan Services yang Dipakai

- [FreeLLMAPI](https://freellmapi.com) — Unified free AI models API (key: freellmapi-d6ffd3f42424f45c3f460a25854164542f6c9ab12d181b85)
- [Vast.ai](https://vast.ai) — Rent GPU untuk mining atau compute
- [GitHub](https://github.com) — Repository hosting & version control
- [Groq Console](https://console.groq.com) — Fast inference (alternatif)
- [Telegram Bot API](https://core.telegram.org/bots/api) — Bot integration

### Official Documentation

- [Hermes Agent Docs](https://hermes-agent.nousresearch.com)
- [SOUL.md Specification](https://hermes-agent.nousresearch.com/docs/soul)
- [Hermes GitHub](https://github.com/NousResearch/Hermes)

### Repo Terkait

- [dhimaszs/How-To-Make-Create-Your-AI-Agent-Smart](https://github.com/dhimaszs/How-To-Make-Create-Your-AI-Agent-Smart) — Repo ini
- [NousResearch/Hermes](https://github.com/NousResearch/Hermes) — Hermes Agent official repo

### Community

- [r/localai](https://reddit.com/r/localai) — Local AI community
- [Vast.ai Discord](https://discord.gg/vastai) — GPU rental community

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

MIT License — Bebas digunakan untuk keperluan pribadi maupun komersial.

---

*Made with ❤️ for the AI Agent community*