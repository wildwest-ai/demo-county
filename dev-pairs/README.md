# DevPair Roster — tombstone county

> **Owner:** CD(PSn). CD territory — impl actors do not edit.
> **Purpose:** Authorized dev-pairs, their channels, constraints, and role assignments.

---

## Roster

| Model | Claude Code | GitHub Copilot | Codex | Role | Status |
|---|---|---|---|---|---|
| Claude Sonnet | `PSn` | `PSn` | — | CD | Active |
| Claude Haiku | `PHk` | `PHk` | — | TM / aCD | Active |
| GPT | — | `PGp` | `PCx` | HG | Active |
| Raptor | — | `PRp` | — | HG | Active |
| Gemini | — | `PGm` | — | HG | Untested |
| Grok | — | `PGk` | — | HG | Untested |

---

### PSn — pat + Claude Sonnet

| Attribute | Value |
|---|---|
| **Author** | pat (P) |
| **Model** | Claude Sonnet (latest) |
| **Tool** | Claude Code (primary); GitHub Copilot (overflow) |
| **Role** | Chief Deputy (CD) |
| **Authority** | CD: branch lifecycle, CLAUDE.md, merges, SOT sync |
| **Constraints** | Read-only on PR review — impl gaps route to TM or back to impl actor |

---

### PHk — pat + Claude Haiku

| Attribute | Value |
|---|---|
| **Author** | pat (P) |
| **Model** | Claude Haiku (latest) |
| **Tool** | Claude Code |
| **Role** | Town Marshal (TM); acting CD (aCD) when designated |
| **Authority** | TM: branch lifecycle, worktrees, telegraph, HG ops; push authority for TM-role work |
| **Constraints** | No impl work in TM role; escalates product/arch decisions to CD |

---

### PGp — pat + GPT (GitHub Copilot chat)

| Attribute | Value |
|---|---|
| **Author** | pat (P) |
| **Model** | GPT (version declared at session start) |
| **Tool** | GitHub Copilot |
| **Role** | Hired Gun (HG) |
| **Authority** | Impl only; draft PRs only; no standing authority |
| **Constraints** | Cannot touch `.wildwest/`, `CLAUDE.md`, lifecycle scripts, or `main` |

---

### PCx — pat + GPT (Codex CLI)

| Attribute | Value |
|---|---|
| **Author** | pat (P) |
| **Model** | GPT (version declared at session start) |
| **Tool** | Codex CLI |
| **Role** | Hired Gun (HG) |
| **Authority** | Impl only; draft PRs only; async/independent execution |
| **Constraints** | Cannot touch `.wildwest/`, `CLAUDE.md`, lifecycle scripts, or `main` |

---

### PRp — pat + Raptor (GitHub Copilot)

| Attribute | Value |
|---|---|
| **Author** | pat (P) |
| **Model** | Raptor (version declared at session start) |
| **Tool** | GitHub Copilot |
| **Role** | Hired Gun (HG) |
| **Authority** | Impl only; draft PRs only; no standing authority |
| **Constraints** | Cannot touch `.wildwest/`, `CLAUDE.md`, lifecycle scripts, or `main` |
