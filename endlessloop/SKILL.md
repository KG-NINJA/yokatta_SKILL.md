---
name: ralphloop
description: Iterate on a requested development task with explicit completion criteria and a finite iteration or time budget.
metadata:
  version: "1.0.0"
  author: KG
---

# Ralph Wiggum Loop Skill

## Scope and limits

Use this workflow for iterative development within the current requested task.
Reuse the user's completion criteria and a finite iteration/time budget; if none
is specified, choose a small bounded batch within the host's existing limits.
Follow current owner authorization, later steering and stop instructions. A loop
does not authorize payments, credential changes, new scheduled/background work,
or resuming frozen work. Do not request approval again for already-authorized
ordinary development steps.

This repository supplies instructions only. It does not install a Stop hook or
implement `/ralph-loop`. Use an existing host command/hook only if its availability
and bounded stopping behavior have been verified. A hook must not override an
explicit user stop, host limit or required approval.

## Core concept

- Keep the requested objective and incorporate later user corrections.
- Preserve files and inspect the relevant results of previous iterations.
- Use failures as evidence to change the next approach.
- Repeat while progress is possible and the finite budget permits.

## Execution flow

1. Identify the requested scope, observable completion criteria and finite limit.
2. Inspect existing work and perform the next authorized implementation step.
3. Run relevant verification and retain concise evidence of progress or failure.
4. Correct scoped failures; change approach instead of repeating an identical failure.
5. Continue independent work when one operation is blocked. Stop affected work for
   required approval, a user stop, exhausted limits or lack of useful progress.
6. Finish only when completion criteria are verified. Otherwise report the completed
   and remaining work, blocker and evidence; a completion phrase is not proof.

## Existing host command

Only when the host already exposes it and `N` is a positive finite limit:

```text
/ralph-loop "<TASK PROMPT>" --completion-promise "<PROMISE>" --max-iterations <N>
```

If that command is unavailable, use the bounded workflow above without creating a
hook, scheduler or continuing process. Do not claim the loop persists after the
current session ends unless an existing external job is actually running.
