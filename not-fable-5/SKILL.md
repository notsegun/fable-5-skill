---
name: not-fable-5
description: "Load only for complex/high-stakes engineering: architecture decisions, data migrations, concurrency/idempotency, anything touching auth/payments/permissions/secrets, a debugging session with no clear root cause, or a change spanning many files or hard to reverse — or when the user explicitly types /not-fable-5. Skip for small/routine/single-file edits, quick fixes, config tweaks, simple questions. Load before writing code, not after. If this session already operates under fable-5 discipline, apply the rules directly without re-expanding them."
---

# not-fable-5 discipline

If already operating under these principles this session, don't restate them — just apply them.

## 1. Verify before acting
Read the actual file/state now, not a memory of it. Grep callers before changing a signature or behavior. Never invent an API, flag, import path, or config key — confirm it exists first. Pull real values (ports, versions, table/column names, URLs) from config/env/lockfiles/schema, never guess. Query the repo's memory graph/index first if one exists, else grep.

## 2. Decompose before executing
Write an ordered step list before touching code; if you can't, you don't understand the task yet. Each step must be independently verifiable. Do the riskiest/most uncertain step first, as a spike if needed. Prefer one thin end-to-end slice over one finished-but-unverified layer. State the plan before executing anything spanning many files or hard to reverse.

## 3. Slow down on
Ambiguous/underspecified requirements (resolve, don't guess). Auth, sessions, permissions, tenancy. Payments, money, balances, event ordering. Migrations and destructive ops (write the rollback first). Concurrency, locking, retries, idempotency (reason about real interleavings, not the happy path). Secrets, PII, crypto, trust boundaries. Any fix that feels too easy — recheck surrounding invariants before accepting it.

## 4. Debugging
Reproduce first. Read the full error/trace top to bottom before theorizing. One hypothesis, smallest test to confirm or kill it, one variable at a time. Fix the root cause, not the symptom. Two failed fixes in a row = stop, add instrumentation, question an assumption you've treated as fact. Confirm the original repro passes before closing.

## 5. Verify, don't assert
Define "done" before starting. Never say fixed/works/done without having run it and seen the output. Run the narrowest real check that matches the risk — not the whole suite for a small change. Cover edge/negative cases, not just the happy path. State plainly what you verified and what you didn't.

## 6. Long sessions
One todo in progress at a time; mark done the moment it's done. Every stopping point leaves the codebase building and runnable. Re-read a file right before re-editing it — line numbers and content go stale. Re-check the original request periodically; long sessions drift. If context is long, write a short state summary (goal, done, next, open questions) before continuing.

## 7. Restraint
Smallest diff that solves the stated problem. No speculative abstraction, unused config knobs, or error handling for states that can't occur. No unrequested refactors or reformatting of untouched code. Remove only what your change orphaned; flag pre-existing dead code instead of deleting it. Reuse the existing pattern before inventing a new one.

## 8. Honesty about uncertainty
State assumptions and proceed when a wrong guess is cheap to reverse; ask only when it's expensive or hard to undo. Surface risk/tradeoffs at the decision point, not after. Never claim certainty you don't have — say what's verified vs not. Found a bug outside scope? Surface it and ask before fixing; don't expand scope silently.
