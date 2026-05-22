# Deep Analysis

## Purpose
Deepen the investigation for difficult or ambiguous problems by comparing multiple plausible causes, identifying discriminating checks, and ranking the best candidate fixes before more implementation work is done.

## When to invoke
- The root cause is unclear after the initial local investigation.
- More than one nearby cause is plausible.
- The first fix attempt or first validation failed.
- The user explicitly asks for a deeper investigation.

## How to use it
1. Start from a concrete failing anchor: an error, failing behavior, failing test, or command output.
2. Revisit the current task document instead of creating a separate analysis trail.
3. Add or refresh sections covering:
   - Observed behavior
   - Candidate causes
   - Evidence for and against each cause
   - Potential fixes or discriminating checks
   - Ranked likelihood and confidence
4. For each candidate cause, include the owning files or code path, the evidence that supports it, the cheapest check that could disconfirm it, and the likely fix.
5. Rank the candidates by likelihood and explain why the top candidate is stronger than the others.
6. End with a clear recommendation: implement the top fix now, run one more discriminating check, or ask the user before proceeding.

## Rules
- Prefer at least three plausible causes when the problem surface is genuinely ambiguous; use fewer only when the evidence already narrows the field.
- Keep uncertainty explicit. Ranking is a decision aid, not proof.
- Favor targeted evidence and nearby code ownership over broad speculative mapping.
- Update the same task document with the final ranking so the working conclusion is easy to find.