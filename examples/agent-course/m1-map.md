# M1 — Map: one agent round trip (example session)

Taught following the style rules in `learner.md`: real-shaped sample and a
real number first, abstraction last. Numbers below are illustrative and
easy to re-derive.

## Default explanation (what you usually get)

> An agent is a system in which a large language model uses tools in a loop
> to accomplish a goal, observing results and deciding next actions.

Correct, and nothing sticks.

## Same idea, taught by the learner's rules

**Conclusion first:** an agent is a `while` loop. The model never runs
anything; it only *asks*. Your code runs the tool and pastes the result back.

**One real-shaped round trip:**

```
→ request 1   messages: [user: "Why does test_parse fail?"]
← response 1  tool_use  {"name": "read_file", "input": {"path": "parse.py"}}
   harness runs read_file, gets 180 lines
→ request 2   messages: [user, assistant(tool_use), user(tool_result: 180 lines)]
← response 2  tool_use  {"name": "run_tests", "input": {"path": "test_parse.py"}}
   ...
← response N  text: "Line 42 splits on ',' but the fixture uses ';'."   (stop)
```

**The number that matters:** every request re-sends the *whole* history.
If each turn adds ~2,000 tokens, turn t sends ~2,000 × t input tokens.
10 turns → 2,000 × (1 + 2 + … + 10) = **110,000** input tokens, not 20,000.
Cost grows ~T², which is why harnesses compact context and cache prefixes.

**Then the abstraction:** loop = (model decides) → (harness acts) →
(result appended to context) → repeat until the model stops calling tools.

## Exercise M1-1 (no looking things up)

An agent runs 10 turns; each turn adds about 2,000 tokens to the history.
Ignoring caching, roughly how many input tokens did it send in total, and
why does that grow faster than the number of turns?

Pass criterion: number within 10% of 110k **and** the reason names
"each request re-sends the full history".

#### My answers

About 20,000 tokens — 10 turns × 2,000.

#### Grading

**Fail.** 20,000 counts only the *new* tokens per turn. Each request
re-sends everything before it: turn 1 sends 2k, turn 2 sends 4k, … turn 10
sends 20k. Sum = 2k × 55 = **110k**, 5.5× your estimate. That's the ~T² growth.
One-line fix: *input per call = whole history so far, not just the new turn.*

Teach-back (5 sentences): explain to a friend why a 20-turn task costs
more than twice a 10-turn task.

Mistake log entry → `learner.md`:
`2026-11-15 · context cost · counted new tokens only, forgot full-history resend · not yet fixed`
