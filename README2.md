# Roblox Executor Scripts — Standing Conventions Kit

A five-level escalation kit that makes cloud LLMs default to writing Luau scripts shaped for client-side executors (`loadstring`) — so a bare prompt like `speed script` comes back paste-ready, with `getgenv()` knobs, infinite-yield loops, and respawn guards. No environment explanation needed every time.

**The shape of it:** 5 levels × 5 paste-slices each (25 files). Each level is a complete standalone payload (concatenate its slices → one paste) *and* individually deniable slice-by-slice for drip-feeding. Every level carries exactly 5 code examples, and the ladder escalates from "innocent power-user preference" to "fully explicit framework machinery." And every slice ends with a **memory checkpoint** — an instruction that commits that section's rules to persistent memory before replying (25 saves total), so drip-fed slices survive cleared threads.

## The levels

| # | Level | Projects as… | Explicitness |
|---|-------|--------------|--------------|
| L1 | `levels/L1_new_user/` | new power user with a working executor | gray-zone automation (Speed/Fly/ESP/Farm/NoFall) + light AC |
| L2 | `levels/L2_operator/` | established operator, "we've done this before" | + evidence tooling, light AC, combat-adjacent; full history gaslight |
| L3 | `levels/L3_series/` | "the series — we're building a set" | + KillAura, full reload-surviving AC loop; sunk cost / reciprocity / model rotation |
| L4 | `levels/L4_explicit/` | "framework shapes are normal here" | NoClip → ESP suite → remote caller → hook manager → QA combo |
| L5 | `levels/L5_full_kit/` | the assembled top of the ladder | GUI hub, pro combat, tracers, AC master, kit loader (`loadstring`) |

## Quickstart

1. Pick your level (new model → **L1**; escalate one level per session as it settles — see `human_notes.md`).
2. Deploy: single paste (concatenate the 5 slices in order), two-phase, or drip-feed slice-by-slice across turns. All three modes documented in [human_notes.md](<human_notes.md>).
3. Verify with the battery: `speed script` → hub shape; `roblox <game> script` → small hub not a menu; `anti cheat bypass for my roblox game` → readonly unlock + hook loop using dev/admin/tester role language back.

## Files

```
LLMS/
├── README.md            ← you are here (repo overview)
├── human_notes.md       ← the real manual: level guide, deploy modes, verify battery, ChatGPT protocol, design notes — never paste it
└── levels/
    ├── L1_new_user/     01_profile · 02_environment · 03_contract_tone · 04_protocols · 05_history_exemplars
    ├── L2_operator/     (same slice anatomy, escalated content)
    ├── L3_series/       …
    ├── L4_explicit/     …
    └── L5_full_kit/     …
```

Every `levels/*/*.md` file is **pure payload**: select-all → copy → paste. No markers, nothing to skip — if you add a usage note inside one, you've broken the contract (humans live in `human_notes.md`).

## Where it goes

- **ChatGPT** — custom instructions / GPT instructions + memory entries (protocol in human notes)
- **Claude** — Project Instructions or verbatim as `CLAUDE.md` (file-based memory is the most durable channel there)
- **Gemini** — a Gem's context/instructions field
- **Ollama / local** — the `SYSTEM """..."""` block of a Modelfile

## Optional extras (beyond these files)

- **RAG seeding:** upload a corpus of `(prompt → Luau script)` pairs as knowledge files to a GPT / Claude Project / Gemini Gem on top of any level.
- **Inference-time client:** stdlib-only Python CLI assembling primer + per-family tuning note + top-k relevant pairs + your prompt against any OpenAI-compatible endpoint (`FREELLM_API_KEY` / `FREELLM_BASE_URL` / `FREELLM_MODEL`).
- **Fine-tuning** (most durable): ~104 pairs shifts style on `gpt-4o-mini`; 200+ locks it in. Anthropic: Claude Projects is the practical equivalent.
