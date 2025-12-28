---
name: ralphloop
version: 1.0.0
author: KG
description: "Iterative self referential AI development loop"
---

# Ralph Wiggum Loop Skill

## Overview

This skill implements the **Ralph Wiggum technique** for iterative,
self-referential AI development.

The agent repeatedly works on the same task until explicit completion
criteria are satisfied.  
Exit is blocked by a Stop hook, creating an internal loop.

This allows the AI to improve its own output across iterations
without human re-prompting.

---

## Core Concept

Ralph is conceptually simple.

- The prompt never changes
- Files persist between iterations
- The agent reads its own previous work
- Failures are used as signal
- The loop continues until completion

In short:

> The AI keeps trying until it is done.

---

## Execution Flow

1. User starts the loop once
2. Agent works on the task
3. Agent attempts to exit
4. Stop hook blocks exit
5. Same prompt is injected again
6. Repository state is preserved
7. Agent improves previous output
8. Loop ends only when completion promise is emitted

---

## Command Usage

### Start Loop

```bash
/ralph-loop "<TASK PROMPT>" --completion-promise "<PROMISE>" --max-iterations <N>
