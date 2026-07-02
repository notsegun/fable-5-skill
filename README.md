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

once installed, this skill is on by default. claude code loads it automatically on any non-trivial engineering task: implementing a feature, fixing a bug, debugging, refactoring, reviewing a diff, or anything spanning more than one file.

to force it explicitly, start your prompt with:

```
/fable-5 <your prompt>
```
