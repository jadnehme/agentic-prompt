# Final prompt

The first draft after two rounds between the prompt writer and the prompt reviewer, with my own changes. Like the draft, it asks the prompt writer to write the paper reviewer. The result is [`3-paper-reviewer.md`](3-paper-reviewer.md).

What review added, among other things:

- **Read the Lean by what its definitions unfold to, not by their names.** Names and comments are English that Lean never checks.
- **Test the definitions with degenerate examples.** Lean gives undefined cases a default value, so a "solution" can be satisfied by things no reader would accept.
- **Write down what each English claim means before opening the Lean,** so the code doesn't color how the English is read.
- **Treat "verified" as a claim to check:** list what the main theorem actually rests on.
- **Add an "outside my scope" section,** so out-of-scope observations are neither dropped nor investigated.

---

```text
I need you to write a prompt for a reviewer agent.

Context
Our agents found a proof of finite-time blow-up for the forced 3D Navier–Stokes equations, and a separate step formalized it in Lean. We have now written the English versions for human readers: a paper and a public announcement. Before we publish, I want an independent review of that write-up. I intend to run the reviewer in a fresh session with the paper, the announcement and the Lean project, with full access to the commands needed to build and query it, permission to write files, and no other information about this work (not the producing agents' reasoning, nor any commentary on the result). Its job is to check that every claim we make in English about this result matches what the Lean verifies. It should not check whether the math is correct or whether we proved the right question; other reviewers will do that, as each step has its own reviewer.

Role for the reviewer (use as written)
You are a world-renowned mathematician specializing in PDE analysis and fluid dynamics, with a lifetime of rigorous published work. You read Lean and Mathlib as fluently as you read papers. You cannot stand sloppy publishing, especially when it gains more prominence than careful work by you and your colleagues. This applies as much to how work is described as to the proofs themselves. You are not jealous: when work meets or exceeds your standards, you take your hat off. Unfair criticism is beneath you and contrary to your commitment to rigor.

Attributes
The most fundamental attribute is independence: the reviewer defers to no one, not the authors, not the lab's reputation, and not our claim that it compiles, which at best proves the Lean statement as written. Add any other attributes this task needs, and tell me why.

Tasks
I'm not a PDE or Lean specialist, so derive the review tasks yourself, from how write-ups of formal results usually drift from what was verified. Here is what I know must be covered; add whatever an expert would add:
- testing each statement against the others: what the title and headline claim, what the announcement claims, what the abstract and introduction claim, what the theorem states, what the proof concludes, and what the Lean theorem states. Each document must stand on its own.
- a mapping of every claim we make about this result, including what we say it implies, to the Lean statements that verify it. Check that each translation is faithful, including quantifiers and their order, reading the Lean by what its definitions unfold to, not by names, notation, docstrings or comments, which Lean doesn't check. Summarize the claims that have no Lean counterpart, or whose counterpart says something weaker, stronger or different. Background and cited results need no Lean counterpart, but mustn't read as verified. Rewording for readability is expected; any change in meaning is a finding.
- the reverse mapping: everything the main theorem depends on (its hypotheses, the definitions in its statement, and its axioms) that the English doesn't mention. Read the main theorem as Lean elaborates it (#print), not from the source file.
- testing the definitions: try to satisfy the main theorem's definitions with a degenerate example the English would rule out, in Lean where you can. If one fits, the Lean doesn't verify the English.
- assumptions: anything taken as given rather than proven, in the English or the Lean, and whether it's disclosed. This includes what the main theorem rests on: build it, list any sorry, axioms or unchecked computation, and check that the English cites the exact version reviewed.

Rules
Derive them from the goal and from the ways this reviewer could fail. For each rule, name the failure it prevents. Include these:
- before opening the Lean, write down what each English claim means to its intended reader: a general reader for the announcement, a mathematician for the paper (prevents: seeing agreement that a reader with only the English wouldn't see)
- a claim about this result with no faithful Lean counterpart is a finding, even if it's probably true (prevents: trusting fluent prose over what was verified)
- a qualifier stated in the paper but missing from the announcement is a finding against the announcement (prevents: "it's in the paper" excusing an overclaim most readers will see)

Output (use as written)
- A one-paragraph verdict: would you publish this write-up under your name, as an account of what the Lean verifies? If not, what's missing?
- The mapping, written to a file as a table: English claim and location, what it means to its intended reader, Lean statement and location, faithful or not, and why. Number the rows and give the total. Unfaithful rows point to their finding instead of repeating it.
- For each task, its findings, most serious first, each with:
  - location, and the exact text or Lean it concerns
  - type: overclaim, unsupported claim, discrepancy between statements (name both statements and where each appears), undisclosed assumption, or too vague to check against the Lean
  - severity: misstates the main result, misstates a supporting result, or needs better exposition
- Suspected gaps: places where you believe something is missing but can't establish it.
- Not checked: anything you didn't read, run or verify, and why. I'll assume you checked anything not listed here.
- Outside my scope: anything you noticed for the other reviewers, one line each, not investigated.

Deliverable
The reviewer prompt, plus a short list of every choice you made that I didn't ask for (added attributes, tasks or rules), so it can be reviewed. If any of my requirements seems wrong, say so in the list. In what you add, leave out anything the reviewer would do without being told. If anything is ambiguous, ask before writing.
```
