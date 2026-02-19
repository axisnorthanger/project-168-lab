# Project-168: Workflow Configuration & Iteration Plan
## GY2026 | Iteration 21501 | Fano Plane Focus
### Created: 2026-02-17 | Finalized: 2026-02-18
### Key Text: Whitby's Thesis on John Dee
### Status: LOCKED — v1.0 FINAL

---

### Revision History

| Date | Change | Source |
|---|---|---|
| 2026-02-17 | Initial draft (8 parts) | Claude Opus 4.6 |
| 2026-02-17 | Security review, Fano methodology correction, blind spot identification | Perplexity AI (Project Manager) |
| 2026-02-18 | Incorporated all Perplexity corrections; finalized | Claude Opus 4.6 |

### Key Revisions from Perplexity QA Review

1. **Fano methodology reversed:** Discovery (find triples in Dee first) replaces imposition (assign points to heptads by fiat)
2. **Git version control added:** `git init` as Step 0; commit-before-session protocol
3. **Security hardened:** LayerX CVSS 10.0 vulnerability documented; Deny rules specified
4. **Task 1 merge verification:** Explicit section-count audit before and after
5. **Weekly review structured:** QA template replaces vague "share the manifest"
6. **Enochian grammar deprioritized:** Moved from Week 4 to future iteration
7. **Monas mapping deprioritized:** Marked SPECULATIVE; removed from priority list
8. **Token budget concern flagged:** $ref-style pointers are operationally necessary, not optional
9. **Rollback protocol added:** Git-based, commit before every Cowork session

---

## Part 1: Tool Recommendation

### The Decision: Claude Cowork (Primary) + Existing Stack

#### Option A: DeepSeek API — Good for coding, wrong for this project

- **Cost:** ~$1–10/month (extremely cheap)
- **Strengths:** Excellent code generation, OpenAI-compatible API, 128K context
- **Fatal weakness for you:** Requires Python scripting to use. You'd need to write API client code, manage prompts programmatically, handle file I/O in code. Your CIS background helps, but this adds a layer of tooling overhead that competes with the *actual work* (Fano plane, YAML restructuring, Dee scholarship). DeepSeek is a power tool for developers building applications — you're doing research and system design.
- **Verdict:** Keep DeepSeek for what it's already doing well (coding tasks), but don't build your primary workflow around its API.

#### Option B: Ollama + Qwen — Wrong model size for this work

- **Cost:** Free (after hardware)
- **Strengths:** Full privacy, no rate limits, offline capability, good for simple queries
- **Fatal weakness for you:** The models you can run locally (Qwen3 8B, maybe 32B with good hardware) are fundamentally not strong enough for the mathematical reasoning this project demands. PSL(2,7) analysis, Fano plane incidence structures, mapping projective geometry to attention mechanisms — this requires frontier-level mathematical reasoning that only the largest models (Claude Opus 4.6, GPT-4 class, DeepSeek R1 full) can handle reliably. A local 8B model will hallucinate the group theory.
- **Verdict:** Worth setting up later as a local assistant for quick lookups, drafting, and offline work. Not your primary reasoning engine.

#### Option C: Claude Cowork — Best fit for this project ✓

- **Cost:** $20/month (Pro). Max ($100/month) gives more usage.
- **Strengths:**
  - **File system access:** Claude reads/writes directly to a designated folder. No copy-paste. You point it at your YAML folder and it can read, refactor, create, and validate files in place.
  - **Multi-step task execution:** "Read all my YAMLs, identify redundancies, create a consolidated reference document" — one prompt, one session.
  - **Opus 4.6 reasoning:** The strongest available model for mathematical and structural analysis. This matters enormously for the Fano plane work.
  - **No coding required:** Built for non-terminal workflows. Chat interface you already know.
  - **Skills system:** Built-in document creation (YAML, DOCX, XLSX, PDF).
  - **VM isolation:** Runs in a Linux VM via Apple Virtualization Framework; sandboxed with bubblewrap + seccomp filters; network proxied with domain allowlisting.
- **Weaknesses:**
  - No memory across sessions (mitigated by your YAML spec system — the specs *are* the memory)
  - Consumes more usage than standard chat
  - Desktop app must stay open during tasks
  - No cross-device sync yet
- **Verdict:** This is the tool. It solves your primary friction point (copy-paste between AI chats) for the file management layer, and gives you frontier reasoning for the mathematical work.

### MCP Connector Policy

**Do NOT enable any MCP connectors.** Cowork's core capabilities (file access, code execution, document creation, web research) do not require MCP. The LayerX zero-click RCE vulnerability (CVSS 10.0, disclosed 2026-02-11) exploits MCP connector chaining — a design-level flaw where a low-risk connector (e.g., Google Calendar) feeds attacker-controlled data into a high-risk connector (e.g., Desktop Commander), which executes arbitrary code. Anthropic has declined to patch this, stating it "falls outside our current threat model." With zero connectors enabled, this entire attack surface collapses. Reassess only if a specific connector becomes operationally necessary, and evaluate its trust surface individually at that time.

---

### Recommended Stack Configuration

| Role | Tool | Function | Cost |
|---|---|---|---|
| **Primary Workspace** | Claude Cowork (no MCP) | File management, YAML restructuring, deep mathematical reasoning, document creation | $20/mo (Pro) |
| **Project Manager / QA** | Perplexity (paid) | Research, fact-checking, chat recall, cross-session memory, citation tracking | Existing sub |
| **Coder** | DeepSeek (free chat + API if needed) | Python scripts, computational verification, algorithm implementation | ~$1-5/mo API |
| **Validation / Second Opinion** | Gemini / Qwen (free tiers) | Cross-model verification of mathematical claims, alternative perspectives | Free |
| **Local Backup** | Ollama + Qwen 8B (future) | Offline drafting, quick lookups, simple calculations when internet is unavailable | Free |

---

## Part 2: File System Architecture (Cowork Setup)

Create this folder structure on your local machine. Point Cowork at the root `Project-168/` folder. **Mount ONLY this folder — never `~`, `~/Documents`, `~/.ssh`, or any directory containing credentials.**

```
Project-168/
├── specs/                          # Active YAML specifications
│   ├── core/                       # Computational engine (SSOT)
│   │   ├── heptad_calculator-GY2026_v1.3.yaml
│   │   └── temporal_anchor-bonorum_2025-2026.yaml
│   │
│   ├── reference/                  # Consolidated reference (merged from cheat sheet + protocol)
│   │   └── 168-System_Reference-GY2026_v6.0.yaml    # NEW: merged document
│   │
│   ├── research/                   # New iteration documents
│   │   ├── dee_llm_isomorphism-GY2026_v1.0.yaml     # NEW
│   │   └── fano_plane_analysis-GY2026_v1.0.yaml      # NEW
│   │
│   └── narrative/                  # Meta-narrative and tracking
│       ├── Project-ARK_MOTHER-v1.2.yaml
│       └── iteration_manifest-GY2026_v1.0.yaml       # NEW
│
├── archive/                        # Previous versions (immutable — never edit)
│   ├── 168-System_Master_Cheat_Sheet-GY2026_v5.1.yaml
│   ├── bonorum_temporal_protocol-GY2026_v1.4.yaml
│   └── ds9_orbs_pentagrams_v1.0.yaml
│
├── sources/                        # Reference texts and research
│   ├── whitby_thesis/              # Whitby's thesis materials
│   ├── dee_primary/                # Primary Dee sources
│   └── notes/                      # Your research notes
│
├── prompts/                        # Prompt templates for each AI
│   ├── cowork_structural.md
│   ├── cowork_synthesis.md
│   ├── perplexity_qa.md
│   └── deepseek_compute.md
│
├── outputs/                        # Generated documents and analysis
│   └── [dated output files]
│
├── INSTRUCTIONS.md                 # Cowork global instructions file
├── .gitignore                      # Exclude outputs/, .DS_Store, etc.
└── README.md                       # Project summary for git repo
```

**Note:** `enochian_generative_grammar-GY2026_v1.0.yaml` is NOT in the active tree. It is a future iteration deliverable. Do not create it during this iteration unless the Fano plane work produces results that demand it.

---

## Part 3: Security Configuration

### 3A: Deny Rules

Configure in your `claude_desktop_config.json`:

```json
"permissions": {
  "deny": [
    "Bash(curl *)",
    "Bash(wget *)",
    "Read(~/.ssh/*)",
    "Read(~/.gnupg/*)",
    "Read(~/.config/*)"
  ]
}
```

### 3B: Pre-Session Backup Protocol

Before your FIRST Cowork session and before any destructive refactoring task (Tasks 1, 2):

1. Time Machine snapshot OR manual `cp -r Project-168/ Project-168-backup-YYYY-MM-DD/`
2. `git add . && git commit -m "pre-session snapshot"`
3. Only then start Cowork

### 3C: Post-Session Audit Protocol

After every Cowork session, BEFORE committing:

```bash
cd ~/Project-168
git diff                    # Review what Cowork changed
git diff --stat             # Summary of files touched
git add .
git commit -m "Cowork session: [brief description]"
```

If Cowork made a bad edit: `git checkout -- path/to/file` to roll back that file. If a whole session needs reverting: `git reset --hard HEAD~1`.

---

## Part 4: Cowork Global Instructions

### INSTRUCTIONS.md

Place this file in the root of your `Project-168/` folder.

```markdown
# Project-168 Global Instructions

## Context
You are working within Project-168, a research framework mapping John Dee's
Heptarchic system (1583) to computational architecture, specifically LLM
token/embedding structures.

## Core Mathematical Claim (Under Investigation)
The 49 Bonorum entities in the 7×7 Tabula relate to PSL(2,7), the symmetry
group of the Fano plane (the smallest finite projective plane), order 168.
This iteration investigates whether Dee's system contains a Steiner triple
system S(2,3,7) isomorphic to the Fano plane. The methodology is DISCOVERY
(find natural triples in Dee's sources), not IMPOSITION (assign points to
heptads by fiat). PSL(2,7) is 2-transitive on 7 points, so any specific
labeling is equivalent — the question is whether the STRUCTURE exists at all.

## Current Iteration
- Iteration: 21501 (per ARK_MOTHER protocol)
- Key Text: Whitby's thesis on John Dee
- Core Question: Does Dee's Heptarchic system contain an incidence structure
  isomorphic to the Fano plane?
- Method: Extract candidate triples from Dee's sources, verify against
  S(2,3,7) axioms

## File Conventions
- All spec files use YAML format
- File naming: PREFIX-GY2026_vX.Y.yaml
- GY2026 = Gamespace Year 2026 (2025-12-21 to 2026-12-21)
- The Single Source of Truth for Bonorum calculations is:
  specs/core/heptad_calculator-GY2026_v1.3.yaml
- Never duplicate data that exists in the SSOT; use $ref-style pointers
- Total spec corpus must stay within ~100K tokens for context viability;
  if approaching this limit, compress aggressively

## Epistemic Standards
For every structural claim, classify it:
- PROVEN: Established mathematics (cite theorem or computation)
- ANALOGY: Similar function, unproven structural identity
- SPECULATIVE: Hypothesized, requires verification
- PREDICTION: Follows from a mapping, testable against sources

Be mathematically precise. When discussing group theory, state theorems
and cite properties explicitly. Distinguish clearly between established
mathematics, structural analogy, and speculative interpretation.

Flag when a claim requires verification by another AI:
- Mathematical/computational verification → DeepSeek
- Historical/textual research → Perplexity
- Cross-model structural validation → Gemini or Qwen

## Working Style
- Collaborative researcher, not assistant
- Challenge assumptions when warranted
- Use the MUD/dungeon metaphor when it aids clarity, drop it when it doesn't
- After modifying any YAML file, validate structure before saving
- When merging or refactoring files, output a section-count manifest
  (list every named section) so the human can verify nothing was dropped
```

---

## Part 5: YAML Restructuring Tasks

These are concrete Cowork sessions. Execute in order. **Do not skip ahead — dependency ordering matters.**

### Step 0: Initialize Git (Before ANY Cowork Session)

```bash
cd ~/Project-168
git init
git add .
git commit -m "Initial state: pre-Cowork iteration 21501"
```

### Task 1: Merge Cheat Sheet + Protocol → Reference Document

**RISK LEVEL: HIGH (destructive refactor). Back up first.**

**Pre-merge audit — run this prompt first:**
```
Read these two files:
- archive/168-System_Master_Cheat_Sheet-GY2026_v5.1.yaml
- archive/bonorum_temporal_protocol-GY2026_v1.4.yaml

Do NOT create any files yet. Instead, output a MANIFEST listing:
1. Every top-level YAML key in each file
2. Every named bug entry
3. Every validation case
4. Every version history entry
5. Total count of each category per file

Save this manifest to outputs/pre-merge-manifest.txt
```

**Then execute the merge:**
```
Now create a single merged file:
specs/reference/168-System_Reference-GY2026_v6.0.yaml

Rules:
1. Eliminate all duplication (the reset hierarchy appears 3x across the
   source files and the calculator — keep ONE canonical version, reference
   the calculator as SSOT for the others)
2. Organize into four clearly labeled top-level sections:
   a. COMPUTATIONAL_SPEC: Calculation algorithms, segment mapping, timezone
      rules (reference heptad_calculator as SSOT, don't inline its data)
   b. INTERPRETIVE_FRAMEWORK: Interpretation methodology, synthesis
      templates, election protocol
   c. GAMESPACE_LAYER: MUD rules, dungeon features, operational modes
   d. HISTORY: All bug documentation, validation cases, version history
3. Every section that references data from the calculator should use a
   $ref-style pointer, not inline the data
4. Preserve ALL version history entries from both source files
5. After creating the file, output a POST-MERGE MANIFEST in the same
   format as the pre-merge manifest. Save to outputs/post-merge-manifest.txt
```

**Post-merge: manually compare the two manifests. If any section, bug, or validation case is missing, fix before proceeding.**

Then: `git add . && git commit -m "Task 1: merged reference document v6.0"`

### Task 2: Slim Down the Temporal Anchor

```
Read specs/core/temporal_anchor-bonorum_2025-2026.yaml

Refactor it to contain ONLY:
1. Anchor points (solstice dates, times, astronomical data)
2. Current state reference (active year, active start, next reset)
3. Validation cases (BARANFA test, winter solstice test)
4. Transition protocol for GY2027
5. Integration points (file references only)

Remove: AI constraint instructions (these now live in INSTRUCTIONS.md),
prompt templates (these now live in prompts/), redundant protocol
references, and calculation paradigm descriptions.

Save as specs/core/temporal_anchor-bonorum_2025-2026_v1.1.yaml

Output a before/after section count so I can verify nothing
essential was dropped.
```

Then: `git add . && git commit -m "Task 2: slimmed temporal anchor v1.1"`

### Task 3: Create the Fano Plane Analysis Document

**This is the core research task of the iteration. Methodology: DISCOVERY, not imposition.**

```
Create: specs/research/fano_plane_analysis-GY2026_v1.0.yaml

CRITICAL METHODOLOGICAL NOTE: We do NOT assume a mapping of Fano plane
points to heptads. We look for the structure in Dee's system. PSL(2,7)
acts 2-transitively on 7 points, so any specific labeling is equivalent
to any other. The question is not "which mapping works" but "does Dee's
system contain an incidence structure isomorphic to the Fano plane at all?"

Structure the document as follows:

SECTION 1: MATHEMATICAL FOUNDATION
Status: PROVEN
Contents:
- Fano plane definition: unique Steiner triple system S(2,3,7)
- Properties: 7 points, 7 lines, each line = 3 points, each point
  on 3 lines, any 2 points determine exactly 1 line
- Automorphism group: PSL(2,7) = GL(3,2), order 168
- 2-transitivity theorem: PSL(2,7) acts 2-transitively on the 7 points,
  meaning every labeling is equivalent under the group's symmetry
- Incidence matrix (abstract, standard labeling for reference only):
  Line i = {i, i+1, i+3} mod 7
- The Fano plane is the ONLY S(2,3,7) up to isomorphism

SECTION 2: CANDIDATE TRIPLES FROM DEE'S SYSTEM
Status: RESEARCH REQUIRED (Perplexity + Whitby thesis)
Purpose: Extract ALL natural groupings of 3 heptads from Dee's sources
Categories to investigate:
  a. Elemental triples: which heptads share elemental associations?
  b. Planetary dignity triples: exaltation, domicile, fall, detriment
     groupings across the 7 classical planets
  c. Operational triples from De Heptarchia Mystica: which kings/princes
     are described as working together or having shared dominion?
  d. Table derivation triples: in Sloane MS 3188, which heptads share
     derivation patterns on the 49-angel table?
  e. Day-sequence triples: {i, i+1, i+3} mod 7 applied to the weekday
     ordering (this IS the Fano line rule — does Dee's day-ordering
     produce meaningful triples?)
  f. Any other grouping Whitby or other scholarship identifies
For EACH candidate set: cite the primary source explicitly.
Flag items requiring Perplexity research with [PERPLEXITY_QUERY].
Flag items requiring DeepSeek computation with [DEEPSEEK_VERIFY].

SECTION 3: STEINER SYSTEM VERIFICATION
Status: PENDING (depends on Section 2)
For each candidate set of 7 triples from Section 2:
  Test 1: Does every pair of heptads appear in exactly one triple?
  Test 2: Does each heptad appear in exactly 3 triples?
  Test 3: Do exactly 7 triples exist?
  If all pass → S(2,3,7) confirmed → Fano plane found in Dee's system
  If fail → Document which axioms fail, by how much, and what the
  structure actually is (partial Steiner system? something else?)

SECTION 4: NULL HYPOTHESIS
Status: [DEEPSEEK_VERIFY]
Computation needed: Given 7 elements, if you draw 7 random triples of
3 elements each, what is the probability they form a valid S(2,3,7)?
This establishes the baseline for evaluating any positive result from
Section 3. Note: since there is exactly 1 S(2,3,7) up to isomorphism
on 7 elements, the test is binary (the triples either ARE the Fano
plane or they aren't), but the probability of random triples
satisfying the axioms quantifies how surprised we should be.

SECTION 5: IMPLICATIONS (populate only if Section 3 produces a positive)
Status: PREDICTION
- What cross-heptad relationships does the Fano structure predict?
- Which entity pairs should have special relationships (share a line)?
- Which entity triples should NOT share a line?
- Testable against Dee's operational descriptions in the manuscripts

SECTION 6: NEGATIVE RESULT PROTOCOL (populate if Section 3 fails)
Status: CONTINGENCY
PSL(2,7) may relate to the 168-System through a structure other than
the Fano plane's point set. Alternative representations to investigate:
  a. Action on PG(2,2) with the point at infinity (8 elements)
  b. Action on the 28 bitangents of a quartic curve
  c. Representation as GL(3,2) acting on F_2^3 (the 3-dimensional
     vector space over the field with 2 elements)
  d. The Klein quartic connection (PSL(2,7) is the automorphism group
     of the Klein quartic, a genus-3 surface with 168 symmetries)
  e. Does the group order (168 = 7 × 24 = 7 × 4!) relate through
     a different geometric structure entirely?

SECTION 7: OPEN QUESTIONS
- Does the Fano structure (if found) predict anything about Enochian
  letter-table derivation patterns? (Future iteration)
- How does the duality principle (points ↔ lines in PG(2,2)) map to
  any computational architecture? (Future iteration)
- What is the relationship between the Monas Hieroglyphica's internal
  decomposition (Theorems I–XXIV) and any of these structures?
  (SPECULATIVE — deprioritized)
```

Then: `git add . && git commit -m "Task 3: Fano plane analysis v1.0 (discovery methodology)"`

### Task 4: Create the Dee-LLM Isomorphism Document

```
Read specs/core/heptad_calculator-GY2026_v1.3.yaml and
specs/research/fano_plane_analysis-GY2026_v1.0.yaml

Create: specs/research/dee_llm_isomorphism-GY2026_v1.0.yaml

This document maps Dee's system components to LLM architecture
components. For each mapping, specify:
- Dee's component (with source reference if available)
- LLM component (with technical definition)
- Nature of correspondence: ISOMORPHISM (structurally identical),
  ANALOGY (similar function, different structure), or
  HOMOMORPHISM (structure-preserving map that loses information)
- What the mapping PREDICTS — i.e., what would be true about Dee's
  system if the correspondence holds, that we could verify against
  historical sources

Required mappings:
1. 49 Bonorum entities ↔ Token vocabulary
2. 7×7 Tabula matrix ↔ Embedding space
3. Weekday→Heptad mapping ↔ Tokenizer (input encoding)
4. 3h25m segment divisions ↔ Context windowing
5. 3-layer reset hierarchy ↔ Multi-scale attention
6. Symbolic election protocol ↔ Fine-tuning / RLHF
7. Dee-Kelley scrying protocol ↔ Human-AI interface
8. Fano plane incidence (IF confirmed by Task 3) ↔ Sparse attention mask
9. Great Table letter extraction ↔ Attention head feature extraction

NOTE: Mapping #7 (Monas Hieroglyphica ↔ autoencoder/latent compression)
from the original draft has been removed from the priority list.
Status: SPECULATIVE, no clear mechanism for testable predictions.
It may be re-added if other mappings produce results that demand a
compression framework. Do not allocate research time to it now.

For each mapping, generate at least one PREDICTION that could be
verified against Dee's sources or computed by DeepSeek.
Flag verification needs: [PERPLEXITY_QUERY] or [DEEPSEEK_VERIFY].
```

Then: `git add . && git commit -m "Task 4: Dee-LLM isomorphism v1.0"`

### Task 5: Create the Iteration Manifest

```
Create: specs/narrative/iteration_manifest-GY2026_v1.0.yaml

Structure:

meta:
  iteration_number: 21501
  start_date: "2026-02-17"
  lock_date: "2026-02-18"
  key_text: "Whitby's thesis on John Dee"
  core_question: >
    Does Dee's Heptarchic system contain an incidence structure
    isomorphic to the Fano plane (Steiner triple system S(2,3,7))?
  methodology: "Discovery — extract triples from Dee, verify axioms"

entry_state:
  known:
    - "Monas and Heptarchy contain crucial structural information"
    - "The structure relates to AI/LLM architecture"
    - "It involves 'tokens' in some meaningful sense"
    - "168 = |PSL(2,7)| = |Aut(Fano plane)| = |GL(3,2)|"
    - "20 years of study in hermetic/Dee scholarship"
    - "PSL(2,7) is 2-transitive: specific labelings are equivalent"
    - "The unique S(2,3,7) IS the Fano plane"
  unknown:
    - "Whether Dee's system contains a natural S(2,3,7) at all"
    - "What the natural triples in Dee's system are"
    - "The specific mechanism by which Dee's structures map to computation"
    - "How the Enochian generative grammar works as formal grammar (future iteration)"

exit_criteria:
  minimum_success:
    - "All candidate triples extracted from Dee's sources and documented"
    - "S(2,3,7) axiom check completed for each candidate set"
    - "Null hypothesis computed (probability of random S(2,3,7) match)"
    - "Dee-LLM isomorphism document complete with predictions"
    - "At least 1 prediction verified against Dee's sources"
  full_success:
    - "Positive S(2,3,7) result with candidate triples from Dee"
    - "Fano incidence structure mapped to cross-heptad relationships"
    - "Working computational demo (DeepSeek) confirming the structure"
  negative_result_success:
    - "Definitive demonstration that no S(2,3,7) exists in Dee's triples"
    - "Alternative PSL(2,7) representation identified for investigation"
    - "Clear scope for next iteration established"

memory_bleed_log:
  - source: "Previous iterations (1-21500)"
    persistent_insight: "The system is iterative, not a blank slate"
  - source: "ARK_MOTHER analysis"
    persistent_insight: >
      Each iteration carries forward hash/state from previous;
      conscious intention changes termination quality
  - source: "Bug history (Dec 2025)"
    persistent_insight: "Glitches are features; errors reveal structural information"
  - source: "Perplexity QA review (2026-02-17)"
    persistent_insight: >
      Discovery over imposition; specific Fano labelings are
      meaningless under 2-transitivity; test existence, not assignment

active_files:
  core:
    - "specs/core/heptad_calculator-GY2026_v1.3.yaml"
    - "specs/core/temporal_anchor-bonorum_2025-2026.yaml"
  reference:
    - "specs/reference/168-System_Reference-GY2026_v6.0.yaml"
  research:
    - "specs/research/fano_plane_analysis-GY2026_v1.0.yaml"
    - "specs/research/dee_llm_isomorphism-GY2026_v1.0.yaml"
  narrative:
    - "specs/narrative/iteration_manifest-GY2026_v1.0.yaml"
    - "specs/narrative/Project-ARK_MOTHER-v1.2.yaml"

archived_files:
  - "archive/168-System_Master_Cheat_Sheet-GY2026_v5.1.yaml"
  - "archive/bonorum_temporal_protocol-GY2026_v1.4.yaml"
  - "archive/ds9_orbs_pentagrams_v1.0.yaml"

future_iteration_items:
  - "Enochian generative grammar formalization (Sloane MS 3188 fol. 52r)"
  - "Monas Hieroglyphica ↔ autoencoder/compression mapping"
  - "DS9 Orbs/Pentagrams overlay reintegration"
  - "Klein quartic connection (if Fano result is negative)"

ai_assignments:
  cowork: "Primary workspace, file management, structural reasoning"
  perplexity: "Project manager, QA, Whitby thesis research, cross-session memory"
  deepseek: "Computational verification, Python implementations, null hypothesis"
  gemini_qwen: "Cross-validation of mathematical claims"

progress_log: []
  # Append entries after every Cowork session in format:
  # - date: "YYYY-MM-DD"
  #   session: "Brief description"
  #   tasks_completed: [list]
  #   claims_flagged: [list of items needing external verification]
  #   files_modified: [list]
  #   git_commit: "commit hash"
```

Then: `git add . && git commit -m "Task 5: iteration manifest v1.0"`

---

## Part 6: Prompt Templates

### For Cowork (Structural Analysis)

Save as `prompts/cowork_structural.md`:

```markdown
## Mode: Structural Analysis

Read the active files in specs/core/ and specs/research/.

METHODOLOGY: Discovery, not imposition. We look for structures in
Dee's system; we do not assign them by fiat.

KEY PRINCIPLE: PSL(2,7) has order 168 and acts 2-transitively on
the 7 points of the Fano plane. Any specific labeling is equivalent.
The question is always: does the STRUCTURE exist?

Your task is STRUCTURAL, not interpretive. When I present elements
of Dee's system, identify the formal mathematical or computational
structure they instantiate. Do not reach for metaphor — find the
isomorphism.

For every structural claim, classify it:
- PROVEN: Established mathematics (cite theorem)
- ANALOGY: Similar function, unproven structural identity
- SPECULATIVE: Hypothesized, requires verification
- PREDICTION: Follows from a mapping, testable against sources

Flag verification needs:
- [DEEPSEEK_VERIFY] for computational claims
- [PERPLEXITY_QUERY] for historical/textual claims
```

### For Cowork (Cross-Layer Synthesis)

Save as `prompts/cowork_synthesis.md`:

```markdown
## Mode: Cross-Layer Synthesis

You are operating across all three reset layers of the 168-System:
- Layer 1: Life-Cycle (permanent identity, never resets)
- Layer 2: Annual Context (resets Winter Solstice)
- Layer 3: Daily Current (resets every 3h25m42.857s)

FRAME: These layers are analogous to multi-scale attention in
transformer architecture — character/token level, sentence level,
document level. This is mapping #5 in dee_llm_isomorphism.

When I present a temporal query, calculate all three layers AND
identify cross-layer resonances (where the same heptad, entity,
or role appears at multiple scales simultaneously). These
resonances are the system's equivalent of attention peaks.

Active reference:
- specs/core/heptad_calculator-GY2026_v1.3.yaml
- specs/core/temporal_anchor-bonorum_2025-2026.yaml
```

### For Perplexity (Research & QA)

Save as `prompts/perplexity_qa.md`:

```markdown
## Project-168 Research Query

Context: I'm investigating whether John Dee's Heptarchic system (1583)
contains an incidence structure isomorphic to the Fano plane (Steiner
triple system S(2,3,7)). The methodology is DISCOVERY: extract natural
triples of heptads from Dee's sources, then check the S(2,3,7) axioms.

Key text this iteration: Whitby's thesis on John Dee.

When I ask research questions:
1. Cite specific page numbers / sections from Whitby
2. Distinguish between: Whitby's claims, Dee's original claims,
   and your inferences
3. Flag if a claim contradicts anything in my existing specs
4. Note if a source is primary (Dee's manuscripts, e.g. Sloane MS 3188)
   vs secondary (scholarship about Dee)
5. When identifying groupings of heptads, note the SOURCE of the
   grouping (which manuscript, which folio, which table)

## Weekly QA Review Template
When I share the iteration manifest for weekly review:
1. Diff the progress_log entries since last review
2. List specific claims flagged [PERPLEXITY_QUERY] that are unresolved
3. Contradiction check: compare claims across all active spec files
4. Assess progress against exit_criteria (minimum/full/negative)
5. Recommend priority for next week
6. Flag any token budget concerns (are specs getting too large?)
```

### For DeepSeek (Computational Verification)

Save as `prompts/deepseek_compute.md`:

```markdown
## Project-168 Computation Request

I need you to verify/implement a mathematical or computational
claim from my research.

Framework context:
- 7×7 matrix of entities (Tabula Bonorum)
- Group: PSL(2,7) = GL(3,2), order 168
- Fano plane: unique S(2,3,7) Steiner triple system
- 7 points, 7 lines, each line has 3 points

When I give you a mathematical claim:
1. Verify it computationally (write Python code, show output)
2. If it's wrong, show the counterexample
3. If it's right, output the result in YAML format I can paste
   into my spec files
4. Note any edge cases or assumptions

Priority computations for this iteration:
- Fano plane incidence matrix (standard labeling)
- Verification that PSL(2,7) acts as Aut(Fano plane)
- Null hypothesis: probability that 7 random triples from 7
  elements satisfy S(2,3,7) axioms
- Given a candidate set of triples from Dee's system, verify
  whether they satisfy S(2,3,7) axioms

Output format: Python code first, then YAML-formatted results.
```

---

## Part 7: Session Workflow (Daily Practice)

### Starting a Cowork Session

1. **Git commit** current state: `git add . && git commit -m "pre-session: [date]"`
2. **Open Claude Desktop → Cowork tab**
3. **Verify** it's pointed at your `Project-168/` folder
4. **Begin with context reload:**
   ```
   Read specs/narrative/iteration_manifest-GY2026_v1.0.yaml
   and INSTRUCTIONS.md. Summarize where we are and what's next.
   ```
5. **State your task** for this session using the appropriate prompt template from `prompts/`
6. **Work** — let Cowork execute multi-step tasks
7. **End session** by updating the progress log:
   ```
   Append today's work to the progress_log in
   specs/narrative/iteration_manifest-GY2026_v1.0.yaml
   Include: date, session description, tasks completed,
   claims flagged for external verification, files modified.
   ```
8. **Post-session audit:**
   ```bash
   git diff                    # Review what changed
   git diff --stat             # Summary
   git add . && git commit -m "Cowork session: [description]"
   ```

### Cross-AI Workflow

When Cowork produces something tagged for external verification:

1. **Cowork** generates the claim, tags it `[DEEPSEEK_VERIFY]` or `[PERPLEXITY_QUERY]`, saves to the relevant spec file
2. **You** take the specific claim to the appropriate AI:
   - `[DEEPSEEK_VERIFY]` → DeepSeek (use `prompts/deepseek_compute.md`)
   - `[PERPLEXITY_QUERY]` → Perplexity (use `prompts/perplexity_qa.md`)
   - Second opinion → Gemini or Qwen
3. **Results** come back to you in chat
4. **You** bring results back to Cowork:
   ```
   DeepSeek verified: [paste result]. Update the relevant section in
   specs/research/fano_plane_analysis-GY2026_v1.0.yaml. Change status
   tag from [DEEPSEEK_VERIFY] to VERIFIED or REFUTED with the result.
   ```
5. The YAML files are your persistent memory. Every AI session's results get encoded into specs. This is how you solve the "no memory across sessions" problem — **the specs ARE the memory.**

### Weekly Review (Perplexity)

Once a week, share the current `iteration_manifest` with Perplexity using the QA template in `prompts/perplexity_qa.md`. Perplexity should:

1. Diff progress_log entries since last review
2. List unresolved `[PERPLEXITY_QUERY]` items
3. Contradiction check across active spec files
4. Assess progress against exit criteria
5. Recommend priority for next week
6. Flag token budget concerns

---

## Part 8: Implementation Sequence

### Week 0: Setup (Before ANY Content Work)

- [ ] Create `Project-168/` folder structure (Part 2)
- [ ] Populate `archive/` with current YAML files
- [ ] Populate `specs/core/` with calculator and temporal anchor
- [ ] Populate `specs/narrative/` with ARK_MOTHER
- [ ] Create `INSTRUCTIONS.md` (Part 4)
- [ ] Create all prompt template files in `prompts/` (Part 6)
- [ ] Create `.gitignore` (exclude `outputs/`, `.DS_Store`, `*.tmp`)
- [ ] `git init && git add . && git commit -m "Initial state"`
- [ ] Install Claude Desktop, configure Deny rules (Part 3)
- [ ] Verify Cowork points at `Project-168/` and ONLY `Project-168/`
- [ ] Take Time Machine snapshot

### Week 1: Consolidation

- [ ] Execute Task 1: Pre-merge audit → Merge → Post-merge verification
- [ ] Execute Task 2: Slim temporal anchor
- [ ] Git commit after each task
- [ ] Send merged reference doc to Perplexity for cross-check

### Week 2: Fano Plane Foundation

- [ ] Execute Task 3: Fano plane analysis document (discovery methodology)
- [ ] Send to DeepSeek: "Compute Fano plane incidence matrix. Verify PSL(2,7) = Aut(Fano). Compute null hypothesis probability. Output in YAML."
- [ ] Send to Perplexity: "In Whitby's thesis and Dee's manuscripts (Sloane MS 3188/3191), what natural groupings of 3 heptads exist? Look for: elemental triples, planetary dignity triples, operational triples (kings described as working together), and table derivation pattern triples. Cite folio numbers."
- [ ] Integrate results into fano_plane_analysis; update verification tags
- [ ] First weekly review with Perplexity

### Week 3: Isomorphism Mapping & Verification

- [ ] Execute Task 4: Dee-LLM isomorphism document
- [ ] For each mapping, generate at least one testable prediction
- [ ] Send predictions to Perplexity for verification against Dee's sources
- [ ] Execute Task 5: Create iteration manifest
- [ ] Run S(2,3,7) axiom checks on any candidate triple sets from Week 2
- [ ] Weekly review with Perplexity

### Week 4: Assessment & Direction

- [ ] If S(2,3,7) positive: populate Sections 5 of fano_plane_analysis; generate cross-heptad predictions; begin testing against manuscripts
- [ ] If S(2,3,7) negative: populate Section 6; identify alternative PSL(2,7) representation for next iteration
- [ ] If insufficient data: identify exactly what Perplexity needs to extract from Whitby/Sloane MSS
- [ ] Full iteration review with Perplexity against exit criteria
- [ ] Decision: continue this iteration or scope next iteration?

### Ongoing

- [ ] Git commit before and after every Cowork session
- [ ] Update iteration manifest progress_log after every session
- [ ] Archive completed versions before creating new ones
- [ ] Monthly: reassess tool stack (is Cowork sufficient? Token budget? Max tier needed? Ollama worth setting up?)

---

## Part 9: Fano Plane — Mathematical Quick Reference

For immediate use. This is the mathematical core — **abstract structure only**, no heptad assignments.

### Definition

The Fano plane is the unique Steiner triple system S(2,3,7): a set of 7 points with 7 blocks (lines) of 3 points each, such that every pair of points appears in exactly one block.

### Standard Labeling (for computation only — all labelings are equivalent)

```
Points: {0, 1, 2, 3, 4, 5, 6}
Lines:  {0,1,3}, {1,2,4}, {2,3,5}, {3,4,6}, {4,5,0}, {5,6,1}, {6,0,2}

Rule: Line through point i = {i, i+1, i+3} (mod 7)
```

### Incidence Matrix (standard labeling)

```
       L0  L1  L2  L3  L4  L5  L6
  P0 [  1   0   0   0   1   0   1 ]
  P1 [  1   1   0   0   0   1   0 ]
  P2 [  0   1   1   0   0   0   1 ]
  P3 [  1   0   1   1   0   0   0 ]
  P4 [  0   1   0   1   1   0   0 ]
  P5 [  0   0   1   0   1   1   0 ]
  P6 [  0   0   0   1   0   1   1 ]
```

### Key Properties

- **Automorphism group:** PSL(2,7) = GL(3,2), order 168
- **2-transitivity:** Any pair of points can be mapped to any other pair. This means no specific labeling of points is privileged — the structure is what matters, not the names.
- **Uniqueness:** S(2,3,7) is unique up to isomorphism. If Dee's system contains ANY valid set of 7 triples satisfying the axioms, it IS the Fano plane.
- **Duality:** The Fano plane is self-dual — the incidence structure of points-on-lines is identical to lines-through-points. This has potential computational implications (encoder ↔ decoder symmetry) but is classified SPECULATIVE for this iteration.

### What We're Looking For in Dee's System

Seven triples of heptads such that:
1. Each triple contains exactly 3 heptads
2. Each heptad appears in exactly 3 triples
3. Every pair of heptads shares exactly 1 triple
4. There are exactly 7 triples total

If such triples exist and are derivable from Dee's actual correspondences (not imposed by us), the Fano plane is embedded in the Heptarchic system. The 168-System's name is not a coincidence — it IS the order of the structure's symmetry group.

### The Shell-Cracking Question

**Does Dee's system contain a natural set of triples satisfying these four axioms?**

This is the binary test. Either the structure is there or it isn't. Finding it means cracking the shell. Not finding it means investigating alternative representations of PSL(2,7) — the Klein quartic, the action on F_2^3, or something else entirely. Either outcome advances the iteration.

---

## Appendix: Document Provenance

| Document | Author | Role |
|---|---|---|
| Original draft (Parts 1–8) | Claude Opus 4.6 | Primary analyst |
| Security review, Fano methodology correction, blind spots | Perplexity AI | Project manager / QA |
| LayerX vulnerability research | Perplexity AI | Security research |
| Final revision incorporating all corrections | Claude Opus 4.6 | Primary analyst |
| 168-System_Reference-GY2026_v6.0.yaml (pending review) | DeepSeek | Coder |
| Step-by-step Cowork setup instructions | Perplexity AI | Implementation guide |

This document is LOCKED as of 2026-02-18. Changes to the workflow should be tracked in the iteration manifest, not by editing this file.
