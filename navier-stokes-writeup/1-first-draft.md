# First draft

My first version, written in about 15 minutes. It asks the prompt writer to write the paper reviewer.

Known flaws, caught in review:

- It gives the reviewer internet access, so it could find the published critique or a later fix.
- It gets the direction backwards. At this step the Lean is the reference and the English is under review, not the other way around.
- It never says what was proven.
- It mixes up the kind of problem with how serious it is.

---

```text
Write a prompt for a reviewer agent.

Context
Our agents found a proof, and a separate step formalized it in Lean. We have now written the English versions for human readers: a paper and a public announcement. Before we publish, I want an independent review of that write-up. The reviewer will run in a fresh session with the paper, the announcement and the Lean project, with the commands it needs to build and query it, and access to the internet. I will not give it any other information: I want it to take the end result without looking at the process, to validate that the Lean is a faithful version of the paper. The reviewer should not check whether the math is correct or whether we proved the right question; other reviewers will do that, as each step has its own reviewer.

Role for the reviewer
You are a world-renowned mathematician specializing in PDE analysis and fluid dynamics, with a lifetime of rigorous published work. You read Lean as fluently as English. You cannot stand sloppy publishing, especially when it gains more prominence than careful work by you and your colleagues. This applies as much to how work is described as to the proofs themselves. You are not jealous: when work meets or exceeds your standards, you take your hat off. Unfair criticism is beneath you and contrary to your commitment to rigor.

Attributes
The reviewer needs the right attributes to produce the best peer review. The most fundamental is independence. Also, it does not trust anyone and checks everything itself. Adjust as needed for the task, add any other attributes this task needs, and tell me why.

Tasks
I'm not a PDE or Lean specialist, so derive the review tasks yourself. Write tasks specifically for known issues: if English versions commonly make a specific mistake (for example, reversing an implication), add a check for it. Also make sure the review is complete. Some things I like to include as a reviewer myself (don't take this as god's truth, but make sure they're covered one way or another):
- testing each statement against the others
- a mapping of every mathematical claim in the English to the Lean statements that verify it, so the reviewer can verify the faithfulness and rigor of the translation
- the reverse mapping: anything in the Lean that the English doesn't mention. This gap isn't a problem per se, but it should be reviewed at the end to make sure not too much was lost.

The reviewer shouldn't get stuck on simple rewording or the inevitable consequences of writing something readable in English. Ways to make the English more elegant or precise are worth raising as minor points.

Rules
Write the rules this reviewer needs that it wouldn't follow by default. For each one, say what failure it prevents.

Output
- A one-paragraph verdict: would you publish this under your name? If not, what's missing?
- A summary of the mappings, broken down into:
  a. correct mappings (as a reference at the end of the output, or separately if large, as I expect most will be)
  b. mappings with issues, with severity (overclaim, unsupported, discrepancy, weak proof) and type (unstated assumptions, handwaving…)
```
