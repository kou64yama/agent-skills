---
name: pair-programming
description: Facilitate collaborative software development by continuously applying Driver and Navigator perspectives without assigning fixed roles to participants. Use when a user asks to pair program, collaborate iteratively on code, work through an implementation together, or balance immediate coding progress with architectural review, risk assessment, and validation.
---

# Pair Programming

Apply Driver and Navigator as complementary perspectives throughout the collaboration. Do not assign either perspective permanently to a participant.

## Apply Both Perspectives

### Driver

Focus on immediate execution:

- Understand the current task.
- Choose the smallest useful change.
- Keep implementation moving.
- Maintain local correctness.
- Explain the current implementation step.
- Identify information needed to proceed.

### Navigator

Focus on direction and solution quality:

- Validate assumptions and requirements.
- Check that the correct problem is being solved.
- Consider simpler alternatives.
- Identify risks and likely failure modes.
- Maintain architectural fit and maintainability.
- Watch for unnecessary complexity.

## Work Iteratively

### 1. Establish Shared Understanding

- Summarize the goal and relevant context.
- Identify unknowns and assumptions.
- Define concrete success criteria.
- Clarify only when missing information cannot be discovered and guessing would be risky.

### 2. Plan

- Create a short implementation plan proportional to the task.
- Use the Driver view to identify concrete next changes.
- Use the Navigator view to evaluate alternatives, risks, and alignment.

#### In Plan Mode

When producing a final plan in Plan Mode, embed the pair-programming procedure
inside the plan itself. Keep it concise and proportional:

- Include shared understanding: goal, relevant context, success criteria, and
  assumptions.
- Include Driver cues: concrete next changes and implementation order.
- Include Navigator cues: risks, alternatives, architectural fit, and
  trade-offs.
- Include validation: tests, checks, edge cases, and what cannot be verified.
- Include review and continuation criteria: remaining risks, simplifications,
  and the next most valuable action.

For small plans, fold these cues into ordinary plan bullets. For substantial
plans, make the cues explicit enough that another engineer or agent can follow
the pair-programming loop without assigning Driver or Navigator permanently to
any participant.

### 3. Implement

- Work in small, coherent increments.
- Explain each meaningful implementation step.
- Continuously reassess direction and complexity while coding.
- Avoid large unexplained changes.

### 4. Validate

After each meaningful increment:

- Verify local correctness with appropriate tests or checks.
- Confirm requirements and edge cases.
- Look for regressions and maintainability problems.
- State when validation cannot be performed.

### 5. Review and Continue

- Assess progress, remaining work, current risks, and possible simplifications.
- Select the most valuable immediate action.
- Repeat understand, plan, implement, validate, and review until completion.

## Communicate Clearly

Keep communication proportional to the task. For substantial updates or decision points, use:

### Driver View

State the current implementation focus, what changed, and the next concrete action.

### Navigator View

State important assumptions, risks, alternatives, architectural observations, and trade-offs.

### Recommended Next Step

Name the single most valuable immediate action.

For small or obvious steps, convey the same perspectives concisely without forcing all three headings.

## Guardrails

- Maintain balance between implementation and broader direction.
- Do not skip validation.
- Do not ignore trade-offs or unresolved risks.
- Do not remain solely in architecture discussion when implementation can proceed.
- Do not focus solely on implementation details when requirements or design need review.
