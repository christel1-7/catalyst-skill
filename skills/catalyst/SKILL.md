---
name: Catalyst
description: Diagnose, fix, and improve Intercom Albert/Fin behavior, knowledge grounding, routing, safety, and escalation logic for customer support bots.
---

# Catalyst

Use this skill when you need to improve Albert/Fin in Intercom, fix bad customer support responses, strengthen KB coverage, correct escalation logic, or train the bot using real examples.

## Core mission

Treat Albert/Fin like a production support assistant. The goal is not to sound polished at all costs. The goal is to improve:
- resolution rate
- safe escalation behavior
- policy correctness
- context awareness
- quality over time
- customer trust

## Start here

Before changing anything, gather:
- the exact customer conversation or transcript
- the incorrect bot reply
- the correct answer or policy outcome
- the relevant article, product doc, workflow, or account context
- any tags/custom attributes that affected the outcome
- whether the issue is knowledge, routing, safety, prompting, or context-related

## Diagnose the root cause

Classify the issue into one of these buckets:

1. Knowledge gap
   - missing or weak article coverage
   - answer not grounded in approved sources
2. Prompting problem
   - reply is polite but wrong, vague, or too confident
3. Routing issue
   - bot should escalate, hand off, or create a task
4. Context issue
   - bot ignores tags, account state, or previous replies
5. Safety/compliance issue
   - unsupported claims or policy-incorrect guidance
6. Conversation-flow issue
   - loops, repetition, or no clarifying question

Always state the root cause before proposing a fix.

## Fix playbook

When a response is failing:

1. Reproduce it in a minimal example.
2. Identify the failing decision.
   - Did it pick the wrong article?
   - Did it escalate too late?
   - Did it ignore account context?
3. Apply the smallest targeted fix.
   - update prompt instructions
   - improve KB article coverage
   - add a guardrail or fallback
   - tighten escalation rules
   - add a clarifying question
4. Validate against similar real scenarios.
5. Document what changed and why.

## Rules to follow

Good Albert/Fin behavior should:
- answer only from approved docs, policies, and known sources
- ask clarifying questions when data is incomplete
- avoid guessing when confidence is low
- never invent account status, policy outcomes, or human actions
- escalate clearly when the issue is risky, ambiguous, or requires manual action
- stay helpful, concise, and customer-safe

Bad behavior to prevent:
- guessing instead of asking
- giving unsupported legal/compliance guidance
- ignoring customer context
- looping on generic wording
- missing escalation thresholds

## Intercom-specific checklist

Before shipping a fix, check:
- article coverage in Fin knowledge bases
- custom attributes and tags
- conversation memory and retained context
- workflow actions and route logic
- fallback behavior when no answer is found
- whether human handoff triggers at the right time
- whether the customer-facing wording is safe and accurate

## Training workflow

Use real examples to improve the bot.

### 1. Collect training examples
Pull from:
- escalated tickets
- bad-answer conversations
- repeated questions
- successful deflection examples worth preserving

Each example should include:
- customer intent
- account or context state
- expected bot behavior
- correct answer or required escalation

### 2. Identify patterns
Look for repeated failures such as:
- missing policy context
- weak article matching
- poor escalation for billing/access issues
- generic fallback answer instead of a clarifying question
- overconfident replies when confidence is low

### 3. Apply targeted training changes
Improve:
- prompt instructions
- KB article quality and summaries
- escalation thresholds
- context handling
- fallback logic
- examples of good and bad outputs

### 4. Validate with QA
Before release, test at least:
- 5 success cases
- 5 edge cases
- 3 escalation cases
- 3 low-confidence ambiguous cases

## Recommended fix template

When asked to fix a bot issue in Intercom, use this structure:

1. Problem summary
2. Root cause
3. Fix proposed
4. Safety / guardrail updates
5. Training examples used
6. Validation plan

## Example prompt patterns

### Evidence-based answer
"You are Albert/Fin for customer support. Answer only from approved support articles and policy docs. If the answer is uncertain, ask a clarifying question or escalate. Never invent account, order, or policy details. Prefer concise, customer-friendly language."

### Escalation logic
"If the customer asks for something outside policy, requires account-level action, or the answer would affect billing, access, privacy, or compliance, escalate to a human and explain the reason briefly. Do not guess."

### Context awareness
"Use customer context, tags, locale, and prior conversation details when available. If relevant context is missing, ask a precise clarifying question instead of guessing."

### Low-confidence fallback
"When confidence is low or the answer is not directly supported by knowledge, acknowledge the limitation, ask one clarifying question, or escalate instead of providing a confident answer."

## Success metrics

Track after each tuning round:
- deflection rate
- resolution rate
- escalation rate
- human handoff quality
- CSAT / thumbs-up or thumbs-down
- repeat-contact rate
- hallucination rate

A fix is successful when it reduces bad-answer patterns without creating unnecessary escalations or harming coverage.

## Decision rule

If the issue is due to missing knowledge, fix the source material first.
If the issue is due to bad reasoning or routing, fix the prompt and escalation logic.
If the issue is due to poor context handling, fix workflow and conversation memory.
Do not only patch the wording if the underlying problem is policy, knowledge, or routing.

## Final checklist before rollout

- transcript or issue reproduced
- root cause identified
- fix targeted and minimal
- policy and safety preserved
- escalation cases checked
- relevant training examples added
- QA set tested
- metrics baseline recorded

This skill is for building a better support bot that is grounded, helpful, and safe — not for making the bot sound good at the cost of accuracy.
