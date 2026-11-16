# custom-tutor

A Claude skill that turns Claude into a personal tutor:

1. **Intake** — five questions about your goal, background, time, and how you learn.
2. **Merge syllabi** — give it 2–4 course links; it builds a topic × course
   matrix, dedupes, cuts what you already know, orders by dependency, and fits
   the plan to your weekly hours. You approve before any teaching starts.
3. **Session loop** — one block per session, taught by your own style rules;
   exercises answered without looking things up; strict grading; 5-sentence
   teach-back; mistakes logged and revisited.

All state is plain Markdown (`learner.md`, `syllabus.md`, `progress.md`), so
any session picks up where the last one stopped, and the tutor gets better at
teaching *you* over time.

## Install

Copy this folder to `~/.claude/skills/custom-tutor/` (Claude Code), then say
"start a course" in any project folder.

## Commands

| Say | What happens |
| --- | --- |
| `start a course` | Intake → syllabus merge → stop for approval |
| `continue the course` / `继续课程` | Grade pending exercises first, else teach the next block |
| `grade` (or paste answers) | Pass / partial / fail per answer + teach-back |
| `end class` / `下课` | One line in `progress.md`, module status updated |

## Example

`examples/agent-course/` merges CMU 11-768, Stanford CS329Z, and Harvard
CS2680 (Fall 2026) into an 8-module, 14-session plan for a learner with a
statistics background and 5 hours a week. `m1-map.md` shows one taught
block: the default explanation vs. the same idea taught by the learner's
style rules, plus an exercise, strict grading, and the mistake-log entry.

## License

MIT
