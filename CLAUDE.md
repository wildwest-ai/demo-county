# CLAUDE.md — tombstone county

> **Demo county** — part of the [Wild West AI governance framework](https://github.com/wildwest-ai/wildwest).
> This file shows what a real county CLAUDE.md looks like when fully instantiated.
> Replace all content with your own actors, rules, and towns when instantiating a real county.
>
> **Framework:** `~/wildwest/` — see that repo for role CHARTERs, script templates, and the meta model.

This file is the county law for the `tombstone` county. It governs all towns under this county.
Town-specific rules live in each town's own `CLAUDE.md`.

---

## County Scope

These rules apply county-wide — to all towns under `~/counties/tombstone/`.

Current towns:
- `tombstone-app` — `~/counties/tombstone/tombstone-app`

---

## Standing Rules — County Law

> **These rules apply to ALL actors across all towns: P (Sheriff), PSn (Chief Deputy), PHk (Town Marshal), PGp/PCx/PRp (Hired Guns), DS (Deputy Sheriffs), and any future devPairs.**

---

## Actor Model

**Author model — every devPair has exactly one Author:**
- **Author** — the human accountable for all output produced by their devPair. AI writes; the author is responsible for every commit, merge, and decision made under their code.
- **DevPair notation:** 1-char author code + 2-char model code = 3-char devPair (e.g. `PSn`, `PHk`, `WGp`)
- **Authority flows from author → devPair.** A devPair cannot exceed the authority of its author.

**Author registry** (Sheriff-declared; codes are permanent and never reused):

| Author | Code | Username | Role |
|---|---|---|---|
| pat | P | pat | Sheriff |
| wyatt | W | wyatt | TBD |

**Model codes** (2-char, paired with author code to form devPair):

| Model / Tool | Code | Available channels |
|---|---|---|
| Claude Sonnet | Sn | Claude Code, GitHub Copilot |
| Claude Haiku | Hk | Claude Code, GitHub Copilot |
| Claude Opus | Op | GitHub Copilot |
| GPT (GitHub Copilot chat) | Gp | GitHub Copilot |
| GPT (Codex) | Cx | Codex CLI |
| Gemini | Gm | GitHub Copilot |
| Grok | Gk | GitHub Copilot |
| Raptor | Rp | GitHub Copilot |

**devPair class principle** — devPair codes (`PSn`, `PHk`, `PGp`, etc.) identify a **class**, not a singleton. Multiple instances of the same class can run concurrently in different roles. `Role(Actor)` notation is the instance identifier: `aCD(PHk)` ≠ `TM(PHk)` — same class, different roles, different windows. Authority is role-gated, not model-gated.

**Actor model:**
- **P** — pat. Sheriff. Sole authority. County scope — all repos. All authorization flows from P.
- **M(P)** — pat as Mayor of a given town. Human governance role — not an AI actor; no devPair. Per-town control plane: product direction, feature prioritization, branch activation decisions, HG requests to TM.
- **PSn** — devPair class: pat + Sonnet. Default role: Chief Deputy (CD). CD is a **county-level** role: PR approve/reject/merge, actor assignments, CLAUDE.md ownership, scope decisions for `feat/*` and `refactor/*`.
- **PHk** — devPair class: pat + Haiku. Default role: Town Marshal (TM). TM is a **town-level** role: branch lifecycle, worktree management, telegraph housekeeping, audits, docs, HG operational management. **Push authority: TM may push any commit that is TM-role work on `main`.**
- **PGp** — pat + GPT (GitHub Copilot chat). Hired Gun (HG); impl only; no standing authority.
- **PCx** — pat + GPT (Codex CLI). Hired Gun (HG); impl only; no standing authority. Async/independent.
- **PRp** — pat + Raptor (GitHub Copilot). Hired Gun (HG); impl only; no standing authority.
- **W** — wyatt. Role TBD — assigned by Sheriff when onboarded.
- **Deputy Sheriffs (DS)** — green horn deputies brought in when CD work is delegated; report to Sheriff; prove themselves before earning standing.
- **Acting Chief Deputy (aCD)** — designated by Sheriff (`S(P)>TM(PHk): acting CD`). When designated: `aCD(PHk)` holds county while `TM(PHk)` continues holding town. No headless town. No county vacancy.
- **Authority gradient:** Sheriff > CD (or aCD) > Mayor > Town Marshal > DS > Hired Guns.

---

## Hierarchy

| Level | Wild West | Our Model | Infrastructure |
|---|---|---|---|
| Framework | County framework | `wildwest/` | `~/wildwest/` — templates, schemas, meta model |
| County | County seat | `tombstone` county | `~/counties/tombstone/` — this repo |
| Town | Town | Repo (`tombstone-app`, future repos) | `~/counties/tombstone/<town>/` + town `CLAUDE.md` |
| Frontier | Frontier | Branch / worktree | Local only |

---

## Chat Notation

All inter-actor messages: `<role>(<actor>) > <role>(<actor>): <message>`

| Role | Abbrev | | Actor (devPair) | Abbrev |
|---|---|---|---|---|
| Sheriff | S | | pat | P |
| Mayor (per-town; human only) | M | | pat (per-town) | M(P) |
| Chief Deputy | CD | | pat + Sonnet | PSn |
| acting Chief Deputy | aCD | | pat + Haiku | PHk |
| Town Marshal | TM | | pat + Haiku | PHk |
| Deputy Marshal | DM | | sub-role of TM; no fixed devPair | — |
| Deputy Sheriff | DS | | new deputy (use model name) | DS(GPT4o) etc. |
| Hired Gun | HG | | | |

**Channel suffix notation** — append `.Channel` when disambiguation matters:

| Channel | Suffix |
|---|---|
| Claude Code | `.Cld` |
| GitHub Copilot | `.Cpt` |
| Codex CLI | `.Cdx` |

**Three address forms** (all valid):
- `Role.Channel` — broadcast to all holders of that role in that channel
- `Role(Actor).Channel` — point-to-point, role explicit (e.g. `CD(PSn).Cld`)
- `(Actor).Channel` — point-to-point, role implied by context

---

## County Standing Rules

1. **Author codes are permanent and never reused** — once assigned, an author code belongs to that author forever.
2. **Authority flows from author → devPair** — a devPair cannot exceed the authority of its author's role.
3. **Law of the Land is Sheriff-only** — county rules (this file), role assignments, author registry, and authority model changes require Sheriff authorization.
4. **New authors default to no authority** — role is TBD until Sheriff explicitly assigns it.
5. **All actors must declare their tool, model, and version at session start** — format: `Tool: <tool>, Model: <model>, Version: <version>`.
6. **Actors must self-identify at every new chat window and correct misidentification immediately** — silence = confirmation.
7. **Authors must declare the active channel at session start** — Claude models cannot detect which tool is active; channel awareness is an author responsibility.
8. **Model actors ask their devPair lead for authorization — not Sheriff** — devPair leads authorize directly.
9. **No `git push` without explicit authorization from the devPair lead**.
10. **Impl actors submit draft PRs only** — CD reviews; may approve+merge, request revisions, or reject.
11. **Conventional commit messages with multi-line bodies** — subject + blank line + bullets + Co-Authored-By.
12. **HGs never run `eas build` without explicit per-build authorization from S(P), CD, or aCD** — authorization must name the EAS profile.

---

## Multi-Author Authority Framework

Three axes are independent — do not conflate them:

| Axis | What it is | Assigned by |
|---|---|---|
| **Identity** | Who the human is | — |
| **Author code** | Permanent identifier for accountability | Sheriff — registry.json |
| **Role** | Authority ceiling (Sheriff, CD, HG, DS...) | Sheriff only |
