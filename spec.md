# SPEC — Cross-Source Intelligence Layer (CSIL)

> Product Requirements Document — v1.0
> Source of truth for all feature planning, task decomposition, and business logic.
> Last updated: 2026-04-01

---

## 1. THE WHITE SPACE WEDGE

### Problem Statement
PKM power users operate across **two disconnected knowledge planes**:

1. **Cloud-structured**: Notion databases, wikis, project boards — rich relational data, no local awareness.
2. **Local-unstructured**: Markdown journals, meeting notes, READMEs, research dumps — fluid and fast, no cloud awareness.

No tool unifies these planes. The user symptoms are:

- **Prompt fatigue**: Manually assembling context from multiple tools before every AI query. Avg PKM power user runs 3–5 tools daily; manually context-switching kills flow states.
- **Context blindness**: Notion AI cannot see your local `notes/` folder. Obsidian copilot plugins cannot see your Notion project trackers.
- **Search fragmentation**: "What did I decide about the API strategy?" requires searching Notion, Markdown notes, and email simultaneously with no unified recall.
- **Reactive-only AI**: Every current tool waits to be asked. No tool proactively surfaces connections, stale threads, or upcoming context packs.

### The Wedge
CSIL is the **cross-source intelligence layer** — a local-first AI daemon that:
1. Indexes both Notion and local Markdown into a single, encrypted, on-device semantic index
2. Answers cross-source questions in natural language with grounded citations
3. Proactively generates a morning intelligence brief BEFORE being prompted

### Core Differentiator
> **"We bridge existing habits; competitors demand migration."**

Users keep Notion. Users keep their Markdown vault. CSIL indexes beneath them, invisibly. Zero workflow disruption. Zero new note-taking app to learn.

---

## 2. MARKET ANALYSIS — FULL DEEP RESEARCH

### 2.1 Market Size & Growth

#### Total Addressable Market (TAM)
The **Personal Productivity Assistant** market sits at **$4.84B in 2024**, projected to reach **$19.63B by 2030** at a **42.1% CAGR**.

**Growth Drivers:**
| Driver | Mechanism | Estimated Impact |
|---|---|---|
| Remote/async work normalization | More tools, more fragmentation, more need for AI synthesis | +8% annual demand |
| LLM commoditization (2024–2026) | Inference costs down 90% since GPT-3 launch → viable local SLM | Unlocks freemium economics |
| 2026 agentic inflection point | Chatbots → proactive agents. Users now acclimated to AI-initiated outputs | Validates Morning Brief as a mainstream feature |
| PKM tool explosion | Notion: 30M+ users. Obsidian: 1M+ users. Logseq, Roam, Bear still growing | Larger TAM from tool proliferation |
| Privacy-driven LLM adoption | Corporate + individual users unwilling to send files to cloud AI | Local-first = competitive advantage, not niche |

**Market Segmentation by Sub-Sector (2026 est.):**
| Segment | Value | CAGR | CSIL Relevance |
|---|---|---|---|
| AI writing assistants | $1.8B | 38% | Adjacent — some overlap with single-tool AI |
| Knowledge management AI | $920M | 51% | **Core TAM** |
| Personal scheduling AI | $640M | 44% | Addressable via Calendar plugin (v0.2) |
| Semantic search tools | $480M | 47% | Core infrastructure overlap |
| AI note-taking | $360M | 49% | Adjacent — we index notes, not create them |

**Geographic Split (2026):**
| Region | Share | Notes |
|---|---|---|
| North America | 41% | Highest PKM tool adoption, enterprise remote work |
| Europe | 28% | High privacy sensitivity → local-first is a strong pull |
| Asia-Pacific | 22% | Rapidly growing but different PKM habits |
| Rest of World | 9% | Emerging |

---

#### Serviceable Addressable Market (SAM)
**Definition**: English-speaking knowledge workers who actively use ≥2 PKM tools and have demonstrated willingness to pay for productivity software.

**Sizing Methodology:**
```
Global knowledge workers (2026):            ~1.25 billion
English-proficient:                          ~400 million
Active PKM tool users (Notion + local tools): ~8%  → ~32 million
Pay for ≥1 productivity SaaS today:          ~40% → ~12.8 million
Use ≥2 disconnected knowledge tools:         ~65% → ~8.3 million
SAM:                                         $1.96B (8.3M users × ~$236 avg annual spend)
```

**SAM Segment Breakdown:**
| User Type | Est. Share of SAM | ARPU | Notes |
|---|---|---|---|
| Solo knowledge workers / freelancers | 40% | $144/yr | Highest churn risk, highest volume |
| In-house researchers / analysts | 25% | $348/yr | High value, lower churn |
| Technical founders / indie hackers | 20% | $240/yr | Early adopters, strong WOM channel |
| Academics / writers | 15% | $144/yr | Price-sensitive, high advocacy |

---

#### Serviceable Obtainable Market (SOM)
| Period | SOM | Active Users | Avg ARPU | Methodology |
|---|---|---|---|---|
| Year 1 (2026) | $4.9M | ~5,000 paying | $980/yr blended | 0.06% SAM. PLG via Hacker News, PKM communities (r/ObsidianMD, Notion subreddit). |
| Year 2 (2027) | $14.7M | ~15,000 paying | $980/yr blended | 0.18% SAM. Expand via influencer PKM channel (YouTube, X). |
| Year 3 (2028) | $39.2M | ~40,000 paying | $980/yr blended | 0.48% SAM. Channel partnerships (Notion App Store listing, Obsidian plugin marketplace). |

---

### 2.2 Unit Economics Deep-Dive

#### Revenue Model
| Tier | Price | MAU Target (Y1) | MRR |
|---|---|---|---|
| **Free** | $0/mo | 20,000 | $0 |
| **Pro** | $12/mo | 4,000 | $48,000 |
| **Teams** | $29/user/mo | 200 users (50 teams) | $5,800 |
| **Y1 Total MRR** | — | — | **$53,800** → ~$646K ARR |

#### Cost Structure (Pro user)
| Cost Item | Monthly Cost/User | Notes |
|---|---|---|
| Cloud LLM inference (BYOK = $0 to us) | $0 | User's own API key. Our target. |
| Cloud LLM inference (non-BYOK, future) | $1.20–$1.80 | Only if we ever offer key-proxying tier |
| Hosting / infra | $0 (local app) | No per-user server cost. |
| Notion API calls | $0 | Free tier sufficient for polling |
| Support amortized | $0.40 | Async support via docs + Discord |
| **Total COGS/user** | **~$0.40** | 96.7% gross margin (BYOK model) |

#### Payback Period (PLG model)
- CAC (Product-Led Growth): $18 blended (content + community, no paid ads year 1)
- MRR per paying user: $12
- Gross margin: 96.7%
- **Payback period: 1.5 months**

---

### 2.3 Macro Forces & Timing

#### Why 2026 Is the Inflection Point
| Force | 2024 State | 2026 State | Impact on CSIL |
|---|---|---|---|
| Local SLM capability | LLaMA 2 — mediocre at reasoning | LLaMA 4 / Phi-4 — GPT-3.5 parity on-device | SLM-first routing is now viable for 70%+ of queries |
| Inference cost | $0.002/1K tokens (GPT-4) | $0.0002/1K tokens (commodity) | Cloud fallback is economically negligible |
| User trust in AI agents | Low — fear of AI editing files | Medium — users comfortable with AI reading/summarizing | Proactive Morning Brief is now acceptable UX |
| Privacy regulation | GDPR enforced in EU | GDPR + US state-level AI privacy laws emerging | Local-first is compliance-competitive advantage |
| Notion API maturity | v1 — limited | Stable, full content coverage | Reliable foundation for source plugin |

---

### 2.4 User Personas (Qualitative)

#### Persona 1 — "The Overloaded Researcher" (Primary)
**Name**: Layla, 32. Independent research consultant.

**Tools**: Notion (client project wikis), Obsidian (personal research notes), Zotero (papers).

**Pain**: Spends 40+ min/day re-reading past notes to answer client questions. Notion AI can't see her Obsidian vault. Has ~3,000 Markdown notes accumulated over 4 years.

**JTBD**: *"When I start a new client project, I want to instantly surface all the notes, ideas, and decisions I've ever made that are relevant — without manually searching three tools."*

**Trigger to pay**: First time CSIL links a local note she forgot about to an active Notion project. "Oh — it found the note I wrote 8 months ago that's directly relevant to this."

**Price tolerance**: $15–20/mo. Currently pays for Notion ($16/mo) and Obsidian Sync ($10/mo).

**Churn risk**: Low — index becomes more valuable over time. High switching cost.

---

#### Persona 2 — "The Technical Indie Hacker" (Early Adopter)
**Name**: Marcus, 28. Solo SaaS founder.

**Tools**: Notion (product roadmap, investor updates), local Markdown in VSCode (technical docs, architecture notes, journal).

**Pain**: Constantly switching context between Notion and his `~/notes` folder. When writing investor updates, can't quickly recall technical decisions from months ago.

**JTBD**: *"When I'm writing, I want my past thinking to be automatically available — not trapped in a different app."*

**Trigger to pay**: Morning Brief that surfaces a stale Notion task he forgot to close, saving him an embarrassing investor follow-up miss.

**Price tolerance**: $12–20/mo. Comfortable with dev tools pricing. Will share on X/HN if impressed.

**Churn risk**: Medium — if Notion ships native local file bridge, will evaluate switching. Our moat: the index has years of his data by then.

---

#### Persona 3 — "The Privacy-Conscious Enterprise Analyst" (Expansion)
**Name**: Priya, 41. Senior strategy analyst at a mid-size firm.

**Tools**: Notion (team workspace), local encrypted Markdown vault (personal strategy notes she won't put in company Notion).

**Pain**: Work AI tools (Microsoft Copilot, Notion AI) require her to put sensitive notes in company-monitored systems. She keeps critical thinking local but loses the synthesis benefit.

**JTBD**: *"I want AI to help me think, but I will never put my personal strategy notes in a company-monitored cloud."*

**Trigger to pay**: Discovers CSIL's local-first + BYOK architecture. The privacy model IS the product for her.

**Price tolerance**: $20–30/mo (company may reimburse as a tool). Would advocate for Teams tier.

**Churn risk**: Very low — privacy requirement makes alternatives structurally unsuitable.

---

#### Persona 4 — "The Prompt-Fatigued Academic" (Volume)
**Name**: James, 26. PhD student.

**Tools**: Notion (reading lists, lab notes), Obsidian (literature review notes, thesis drafts).

**Pain**: Every AI interaction requires copy-pasting context from notes. ChatGPT doesn't know what he read last week. Obsidian plugins are buggy and require configuration.

**JTBD**: *"When I ask an AI a question about my research area, I want it to already know my notes — I'm tired of building the context myself."*

**Trigger to pay**: Free tier alone (local Markdown index). Likely upgrades to Pro for Notion sync after 2 weeks.

**Price tolerance**: $8–12/mo. Price-sensitive but will pay for anything that eliminates prompt assembly.

**Churn risk**: Medium — graduates and context changes. But strong community WOM in academic circles.

---

### 2.5 Jobs To Be Done (JTBD) Framework

| When... | I want to... | So I can... | CSIL Feature |
|---|---|---|---|
| Starting a new project | Surface all past related notes/decisions | Avoid reinventing the wheel | Cross-source query engine |
| Opening my laptop | Know what needs attention today | Start my day focused, not reactive | Morning Brief |
| Writing a document | See related notes appear automatically | Write with full context, not just memory | Proactive context packs |
| Asking a question | Get an answer grounded in MY knowledge base, not ChatGPT's training data | Trust the answer | Grounded RAG with citations |
| Reviewing past decisions | Find the exact note where I decided X | Recall without manual search | Semantic search |
| Collaborating in Notion | Know if my local notes already contain relevant thinking | Share prior art without manual lookup | Cross-source query with Notion output |

---

## 3. COMPETITOR COUNTER-MOVES — DEEP TEARDOWN

### 3.1 Notion AI

**Product Reality (April 2026)**:
- AI is embedded directly in the editor — inline completions, page summaries, Q&A within a Notion workspace.
- Q&A draws from pages and databases in the user's connected workspace only.
- No access to local files, external Markdown vaults, or non-Notion data.
- Pricing: Included in Notion Plus ($10/mo) and Business ($18/mo/user). No standalone AI tier.

**Structural Weaknesses**:
| Weakness | Evidence | CSIL Exploit |
|---|---|---|
| Ecosystem lock-in | Users must keep ALL knowledge in Notion for AI to be useful | We index Notion as just one source among many |
| No local file awareness | Hard-coded to Notion's graph only | Our core value prop — the bridge |
| Privacy: Notion owns the training data | ToS allows using content to improve models (opt-out exists but non-obvious) | Our zero-retention + BYOK is a direct counter-narrative |
| Reactive-only AI | No proactive surfacing of connections | Morning Brief is structurally different from anything Notion ships |
| Weak at cross-workspace synthesis | Q&A limited to one workspace | We unify across workspaces AND local files |

**Anticipated Competitive Response (12–18 months)**:
- *Most likely*: Notion ships a "Local Files" connection that can index a folder on your Mac. Impact: Medium. Our response — we'll already have 12+ months of index history, deeper semantic linking, and the Morning Brief. Import ≠ intelligence.
- *Less likely*: Notion acquires an Obsidian-like local app. Impact: High. Our response — go multi-platform aggressively and build API partnerships with other PKM tools before Notion can lock them out.

**Counter-Positioning Statement**: *"Notion AI is smart inside Notion. CSIL is smart across everything."*

---

### 3.2 Mem

**Product Reality (April 2026)**:
- AI-native note-taking app with automatic linking and semantic search.
- Heavy AI summarization and connection-surfacing built into the notes UX.
- ChromaDB-style vector search under the hood, cloud-hosted.
- Pricing: $14.99/mo (individual), $24.99/mo (Pro).

**Structural Weaknesses**:
| Weakness | Evidence | CSIL Exploit |
|---|---|---|
| Requires full migration | Users must move ALL notes into Mem to get AI benefits | We require zero migration |
| No Notion integration | Mem and Notion are competitors, not complements | We bridge both — users keep Notion |
| Cloud-only | All notes stored on Mem's servers | Our local-first architecture is a direct privacy counter |
| Single-tool vision | Solves note-taking AI, not multi-tool synthesis | Our positioning: "The intelligence layer BELOW your tools" |
| Churn on migration failure | Users who try to migrate but don't complete → cancel | We never require commitment — adoption is additive |

**Anticipated Competitive Response**:
- *Most likely*: Mem ships a Notion sync. Impact: Medium. Our response — we'll have more sources, a proactive layer, and better privacy by then.
- *Our moat over Mem*: We explicitly do NOT want to be a note-taking app. "Bridge existing habits" is a cleaner positioning than asking users to switch.

**Counter-Positioning Statement**: *"Mem asks you to move in. CSIL moves into where you already live."*

---

### 3.3 Google Gemini (Personal Intel / Workspace)

**Product Reality (April 2026)**:
- Gemini 1.5 Pro (2M token context window) integrated into Google Workspace.
- Gemini Personal: experimental feature connecting Gmail, Drive, Calendar, Docs into a personal intelligence layer.
- Horizontal breadth — connected to all Google properties.
- Pricing: Bundled with Google One AI Premium ($19.99/mo).

**Structural Weaknesses**:
| Weakness | Evidence | CSIL Exploit |
|---|---|---|
| Google ecosystem lock-in | Only useful if you live in Google's stack | We work with Notion + local Markdown (dominant tools outside Google Workspace) |
| Privacy structurally compromised | Google's business model is ad-based data utilization | Our local-first + BYOK is not just a feature — it's a trust story that Google cannot replicate without destroying their ad business |
| No deep PKM understanding | Gemini is a horizontal AI, not a PKM-specialized tool | Our chunking, linking, and Morning Brief logic is purpose-built for PKM workflows |
| Blind to local files (non-Drive) | Only indexes Drive-hosted docs | We index local Markdown, Obsidian vaults natively |
| No Notion integration | Google and Notion are competitors | We explicitly bridge the Notion↔Local gap |

**Anticipated Competitive Response**:
- *Most likely (2027)*: Google ships "Gemini for Files" that can index local folders via a desktop agent. Impact: High. Our response — ship Teams tier, deepen cross-source graph, and make local-first privacy story even more explicit. Google's agent will phone home; ours will never.
- *Nuclear scenario*: Google acquires Notion. Impact: Severe short-term. Our response — pivot to "Google-free PKM layer," accelerate Obsidian/Logseq integrations.

**Counter-Positioning Statement**: *"Gemini knows everything about you — and so does Google. CSIL knows everything about you, and only you do."*

---

### 3.4 Obsidian + AI Plugins (Community Ecosystem)

**Product Reality (April 2026)**:
- Obsidian core: local Markdown vault manager, no AI.
- Community plugins: Copilot plugin, Smart Connections (semantic search), various LLM integrations.
- Plugins are inconsistent in quality, require technical setup, no central AI orchestration.
- No Notion integration in core. Community plugins exist but fragile.
- Pricing: Obsidian free (personal), $50/yr Sync, $16/yr Publish.

**Structural Weaknesses**:
| Weakness | Evidence | CSIL Exploit |
|---|---|---|
| Plugin fragmentation | 15+ competing AI plugins, incompatible configs | We provide one unified, maintained AI layer |
| No cloud source integration | Core team explicitly avoids cloud sources | We are the Notion bridge Obsidian will never ship officially |
| Technical barrier | Plugin setup requires API key config, JSON editing | Our installer targets non-technical users |
| No proactive features | All Obsidian AI is reactive/on-demand | Morning Brief is structurally unavailable to Obsidian plugins |
| Community maintenance risk | Popular plugins go unmaintained | We are a maintained commercial product |

**Relationship Strategy**: Obsidian is a **SOURCE**, not a competitor. We consume Obsidian vaults as a first-class source plugin. Obsidian's community is a key **distribution channel** (r/ObsidianMD, Discord). We should be in the Obsidian plugin directory.

**Counter-Positioning Statement**: *"Obsidian is your vault. CSIL is the AI that reads it — plus everything else."*

---

### 3.5 Microsoft Copilot (for Personal Use)

**Product Reality (April 2026)**:
- Microsoft 365 Copilot: enterprise-focused, $30/user/mo.
- Copilot Free: consumer tier, limited to Bing/web context.
- Windows integration: can access local OneDrive files.
- Does NOT index local Markdown files outside OneDrive.
- Pricing: $30/mo (M365 Copilot). Prohibitive for individual PKM users.

**Counter-Positioning Statement**: *"Copilot is for your 9-to-5. CSIL is for your thinking."*

---

### 3.6 Competitive Positioning Map

```
                    HIGH PRIVACY
                         │
        CSIL ────────────┼──── (no competitor here)
     (local-first,       │
      cross-source)      │
                         │
BROAD ───────────────────┼─────────────────── SPECIALIZED
(many tools)             │                    (one tool)
                         │
  Google Gemini ─────────┼──── Notion AI ─── Obsidian Plugins
  Microsoft Copilot      │        Mem
                         │
                    LOW PRIVACY
```

**CSIL occupies the upper-left quadrant: high privacy + cross-source breadth. No competitor is in this space.**

---

### 3.7 Moat Analysis

| Moat Type | Description | Time to Copy (Competitor) |
|---|---|---|
| **Data network effects** | Index grows richer with every new note added. User's personal semantic graph has years of their thinking embedded. | Non-copyable (it's the user's own data history) |
| **Cross-source graph density** | More sources connected → more links discovered → higher perceived value. 4 sources feels 10x more valuable than 1. | 12–18 months for a well-funded competitor to match functionally |
| **Privacy trust capital** | Being verifiably local-first, open-source-auditable is a trust asset. Can't fake local-first. | Never — a cloud-first company can't credibly go local-first without destroying their cloud product |
| **Morning Brief stickiness** | Once users rely on daily briefing, it becomes a habit. Breaking the habit requires a direct replacement, not just a feature. | 6–12 months to build; years to match habituation |
| **Plugin ecosystem** | Each source plugin (Obsidian, Logseq, etc.) is a distribution node into that community | 6–12 months to match breadth |

---

## 4. CORE FEATURES

### 4.1 Unified Semantic Index
*(see constitution.md §4 for engineering spec)*

| Requirement | Detail |
|---|---|
| Sources v1 | Notion pages/databases, local Markdown (flat + Obsidian vaults) |
| Chunking | Semantic (sentence boundaries). 512 tokens max. 64-token overlap. |
| Embedding | Local: `all-MiniLM-L6-v2`. Cloud: OpenAI `text-embedding-3-small` (BYOK). |
| Dedup | SHA-256 content hash. Skip re-embedding unchanged content. |
| Incremental sync | Poll Notion every 5 min (configurable). Watchdog on local FS for real-time. |
| Metadata | Source type, source ID, title, path, last_modified, content_hash, chunk_index. |

### 4.2 Cross-Source Query Engine

| Requirement | Detail |
|---|---|
| Input | Natural language via CLI or local web UI. |
| Retrieval | Top-K (default K=5) cosine similarity. Re-rank by MMR. |
| Context assembly | Concatenate chunks. Prepend metadata. Cap at 4,000 tokens. |
| Citation | Every answer includes clickable source refs (Notion URL or local path + line). |
| Fallback | If no chunk similarity >0.3: "I don't have information on this in your knowledge base." |

### 4.3 Proactive Morning Layer (FLAGSHIP FEATURE)

**Business Logic**: The system generates a personalized intelligence brief every morning WITHOUT user prompting.

#### Brief Contents
| Section | Description | Source |
|---|---|---|
| Unresolved threads | Notion tasks/pages updated yesterday with no follow-up scheduled | Notion + SQLite metadata |
| Cross-source links | New semantic connections found between Notion content and local notes | Vector similarity across sources |
| Stale items | Notes >14 days untouched with high similarity to recent activity | Metadata age + vector similarity |
| Today's context pack | Pre-assembled docs relevant to today's calendar events | Calendar plugin (v0.2) / manual |
| 24h digest | Summary of what changed across all sources since last brief | Incremental sync log |

#### Trigger Logic
| Trigger | Behavior |
|---|---|
| Scheduled (cron) | Default 07:00 local time. Configurable. Cache result. |
| Laptop-open | Detect wake-from-sleep. Generate if no brief today. Serve cached if exists. |
| Manual | `csil brief` — force regenerate. |
| API | `POST /brief/generate` for future integrations. |

#### Constraints
- **Read-only**: Never modifies user content during brief generation.
- **Performance**: Must complete in <60 seconds on 16GB RAM, no GPU.
- **Token budget**: Max 5,000 input tokens to cloud LLM per brief.
- **Output**: Markdown. Rendered in terminal (`rich`) or local web UI.
- **Caching**: Store brief as encrypted local file. Serve cached version to repeat requests same day.

### 4.4 Source Plugin System

| Plugin | Priority | Sync Method |
|---|---|---|
| `notion` | P0 — Launch | Async poll via official API. OAuth or integration token. |
| `local_markdown` | P0 — Launch | `watchdog` FS events + initial full scan. |
| `obsidian_vault` | P1 — Fast follow | Local Markdown with `[[wikilink]]` resolution. |
| `google_docs` | P2 — Future | API poll. BYOK OAuth. |
| `calendar` | P2 — Future | Google Calendar / .ics. Read-only. |

**Plugin Interface** (`core/plugins/abstract.py`):
```python
class AbstractSource(ABC):
    async def connect(self, config: SourceConfig) -> bool: ...
    async def poll(self) -> list[ChangeEvent]: ...
    async def fetch_content(self, source_id: str) -> Document: ...
    async def healthcheck(self) -> SourceStatus: ...
```

---

## 5. SECURITY MODEL

### 5.1 Threat Model

| Threat | Severity | Mitigation |
|---|---|---|
| API key exfiltration | Critical | Keys stored in OS keyring via `keyring`. Never in plaintext files. |
| Content leakage via LLM API | High | `store: false` enforced on all API calls. Audit log on every call. |
| Local index theft (stolen device) | High | SQLite encrypted via `sqlcipher`. Vector store AES-256-GCM. |
| MITM on API calls | Medium | TLS 1.3. Certificate pinning for Notion + LLM endpoints. |
| Prompt injection via Notion content | Medium | Sanitize all ingested text. Strip executable patterns before LLM context assembly. |
| Over-permissioned Notion integration | Low | Request minimum scopes: read-only content, no user PII. |

### 5.2 Data Classification & Retention

| Data Type | Location | Encryption | Retention |
|---|---|---|---|
| Raw content (text) | In-memory only | N/A (transient) | Purged after chunking |
| Embeddings | Local vector store | AES-256-GCM | Persistent, user-deletable |
| Metadata | Local SQLite | `sqlcipher` | Persistent, user-deletable |
| API keys | OS keyring | OS-managed | Until user revokes |
| LLM audit logs | Local SQLite | `sqlcipher` | 90 days (configurable) |
| Morning Brief cache | Local file | AES-256-GCM | 24 hours |

### 5.3 User Data Rights
- `csil data export` — exports all metadata and index stats as JSON. Raw content not stored; cannot export what's not held.
- `csil data purge` — deletes all local index, cache, and audit logs. Source data (Notion, local files) untouched.
- `csil audit show` — displays full LLM call audit log (timestamp, provider, token count, content hash only).

### 5.4 Compliance Posture
- **GDPR**: All data local. No processor relationship with CSIL. User is sole controller.
- **CCPA**: No sale of personal data — nothing leaving the device to sell.
- **SOC 2 (future Teams tier)**: Audit log, encryption at rest, access controls already in architecture.

---

## 6. NON-FUNCTIONAL REQUIREMENTS

| NFR | Target | Measurement Condition |
|---|---|---|
| Cold start (first index) | <5 min for 1,000 docs | M1 MacBook Air 16GB |
| Incremental sync latency | <10 sec per changed doc | FS event timestamp to index commit |
| Query response — local SLM | <3 sec | End-to-end: retrieval + generation |
| Query response — cloud LLM | <8 sec | Including network round-trip |
| Morning Brief generation | <60 sec | 16GB RAM, no GPU |
| Memory footprint (idle daemon) | <200 MB | Background steady-state |
| Disk usage (index) | ~1 MB per 1,000 chunks | Vector store + metadata combined |

---

## 7. MVP SCOPE — v0.1 LAUNCH

### In Scope
- [x] Local Markdown source plugin (`watchdog` + initial scan)
- [x] Notion source plugin (async poll, integration token or OAuth)
- [x] Unified semantic index (ChromaDB + local `all-MiniLM-L6-v2` embeddings)
- [x] Cross-source query engine (CLI: `csil ask "..."`)
- [x] Morning Brief (scheduled + manual: `csil brief`)
- [x] BYOK configuration for OpenAI / Anthropic (CLI: `csil config set-key`)
- [x] Token budget system with daily and monthly limits
- [x] Encrypted local storage (SQLite + vector store)
- [x] Audit log (`csil audit show`)

### Out of Scope (v0.1)
- [ ] Local web UI — v0.2
- [ ] Calendar integration — v0.2
- [ ] Obsidian `[[wikilink]]` resolution — v0.2
- [ ] Google Docs plugin — v0.3
- [ ] Team features / shared knowledge graphs — v1.0
- [ ] Mobile app — future
