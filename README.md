# custom-tutor

**Courses are raw material, not a route.** Don't follow one course end to
end: hand an AI 2–4 good courses plus your background, and let it be your
editor (pick, cut, order) and your tutor (teach, test, grade).

A Claude skill that turns Claude into that personal tutor:

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

## No install: copy a prompt

Don't use Claude Code? Paste the prompt in [`prompt.md`](prompt.md)
(English and Chinese) into any AI chat. You get the same three steps; the
skill just keeps the state in files for you.

## Install (Claude Code)

Copy this folder to `~/.claude/skills/custom-tutor/`, then say
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
