# fable-5

a claude code skill that pushes any model toward fable 5 level engineering discipline: read before acting, decompose before executing, verify before claiming done.

built for [claude code](https://claude.com/product/claude-code) (anthropic), works with claude sonnet, opus, and haiku, and any other agent runtime that supports the same skill format.

## disclaimer

this skill does not guarantee your model performs at fable 5's level. it tries to force the model to follow the policies and structures fable 5 would use: reading real files before editing, tracing call sites before changing behavior, decomposing work into verifiable steps, and refusing to say "done" without evidence. results depend on the underlying model.

## install

copy the `fable-5` folder into your skills directory:

```
git clone https://github.com/notsegun/fable-5-skill.git
cp -r fable-5-skill/fable-5 ~/.claude/skills/fable-5
```

## usage

this skill does not load on every task. claude code only reaches for it on complex or high-stakes engineering work: architecture and design decisions, data migrations, concurrency or idempotency work, anything touching auth, payments, permissions, or secrets, a debugging session with no clear root cause yet, or a change that spans many files or is hard to reverse.

for small, routine, or single-file edits, quick fixes, config tweaks, or simple questions, it stays out of the way.

to force it explicitly on any task, start your prompt with:

```
/fable-5 <your prompt>
```
