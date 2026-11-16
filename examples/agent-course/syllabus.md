# Merged syllabus (example): AI agents, three courses → one plan

Fetched 2026-11-15 from the official course pages.

## Source courses

| Course | Institution · term | URL | Recorded? |
| --- | --- | --- | --- |
| 11-768 AI Agents (Neubig, Fried) | CMU · Fall 2026 | https://cmu-agents.com | Yes (recording per lecture) |
| CS329Z Engineering AI Agents (Diyi Yang, Michael Ryan, John Yang) | Stanford · Fall 2026 | https://cs329z.stanford.edu | Yes (video links per lecture) |
| CS2680 Modern AI Systems: Agents and System Optimizations (Juncheng Yang) | Harvard SEAS · Fall 2026 | https://cs2680.com | Slides posted; recordings not stated |

Each course has a different centre of gravity:
CMU = capabilities + **training (SFT/RL)**; Stanford = **engineering + data + evals**;
Harvard = **using coding agents → cost → serving systems**.

## Topic × course matrix

| Topic | CMU 11-768 | Stanford CS329Z | Harvard CS2680 | Picked source | Note |
| --- | --- | --- | --- | --- | --- |
| What is an agent | L1 | Sep 23 | Sep 2 | Stanford | Video + readings (Kapoor "AI Agents That Matter") |
| LLM internals for builders | — | Sep 28 | Oct 19 | Stanford | Compressed: learner has ML background |
| Using a coding agent well | L6 | Nov 30 | Sep 9, Sep 14 · A1 Mads-Lens | Harvard | Only course that starts from Claude Code usage |
| Tool use / function calling / MCP | L2 | Oct 5 | Sep 16 | CMU | |
| Context management | L3 | Sep 28 (part) | Sep 16 | CMU | |
| Design patterns (ReAct, Reflexion, CodeAct) | L5 | Oct 12 | — | Stanford | |
| Build the loop from scratch | A1 Harness | HW1 (no frameworks) | A2 Mads-Loop | CMU A1 | All three assign it — strongest signal in the matrix |
| Memory & skills | L4 | Oct 14 | Sep 28 | CMU | |
| Multi-agent | L5, L18 | Oct 19 | Sep 23 | Stanford | Optional |
| RAG | — | Sep 30 | — | Stanford | Optional |
| Agent evaluation | A2 Eval | Nov 4, Nov 11 (+ Terminal-Bench, SWE-bench guests) | Sep 30 | Stanford + CMU A2 | Lectures from Stanford, assignment from CMU |
| Data for agents (traces, flywheels) | — | Oct 28, Nov 2 | — | Stanford | Only Stanford covers it |
| Cost & performance | — | Oct 21 (optimization) | Oct 7 · A3 Mads-Opt | Harvard | |
| Training: SFT / RL | L8, L9, L11, L12 · A3 Training | Oct 21 (part) | — | CMU | Optional (needs GPU) |
| Safety | L13 | Nov 18 | Oct 14 | Stanford | |
| Observability & monitoring | L15 | — | — | CMU | |
| LLM serving (batching, KV cache, spec. decoding, quantization) | — | — | Part II, A4–A5 | — | **Cut** |
| Domains: computer use, deep research, personal agents | L7, L10 | Dec 2 | — | — | **Cut** |
| Search: reranking, tree search | Search 1–2 | — | — | — | **Cut** |

## Cut (and why)
- **LLM serving / GPU systems** (Harvard Part II): strong material, but off the goal
  (build + evaluate agents) and too heavy for 5 h/week. Revisit after the plan.
- **Application domains, search**: interesting, not needed for the deliverable.
- **Statistics of evals**: learner already has it; eval blocks skip straight to verifier design and pass^k.

## Modules

| Module | Topic | Blocks | Deliverable | Pass criterion | Status |
| --- | --- | --- | --- | --- | --- |
| M1 | Map: anatomy of an agent + LLM internals (compressed) | 1 | One-page diagram of one real agent round trip | Every arrow labeled with what is sent | Not started |
| M2 | Using a coding agent like a power user | 1 | Log of one real task: prompts, tool calls, tokens | Can say where the tokens went | Not started |
| M3 | Build the loop: tools, context, patterns | 3 | ~150-line agent, no frameworks | Solves 5 small tasks; logs every tool call | Not started |
| M4 | Memory & skills | 1 | Add one skill + one memory file to the M3 agent | Measurable change on one task | Not started |
| M5 | Agent evals | 3 | 15-task eval, k = 3, pass^k, cost per task | Detects a deliberately broken harness (CI excludes 0) | Not started |
| M6 | Cost & optimization | 2 | Accuracy vs. cost Pareto plot, 3 configs | Every claim backed by own numbers | Not started |
| M7 | Training: SFT / RL (optional) | 2 | LoRA before/after on one task | Holdout CI reported | Not started |
| M8 | Safety + observability | 1 | Trace table for 10 runs | Any run's full trace is one click away | Not started |

14 blocks ≈ 9–10 weeks at 1–2 blocks/week.

Fixed order: M3 before M5 (need an agent to evaluate); M5 before M6 (need a ruler before optimizing).
