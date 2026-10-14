# Reviewing a write-up against its Lean proof

On September 8, 2026, OpenAI announced an AI-produced proof about the Navier–Stokes equations, checked in Lean. A month later, Bastounis, Circelli and Hansen showed that the Lean proof doesn't correspond to the English paper ([arXiv 2610.08144](https://arxiv.org/abs/2610.08144)).

These files record how I built a reviewer for one step of such a project: **does everything said in English match what the Lean verifies?** They also record how I tested it on OpenAI's actual materials.

Article: [Technically correct, completely wrong](https://www.linkedin.com/pulse/technically-correct-completely-wrong-whos-reviewing-your-jad-nehme-7kmac/)

## The three roles

- **Prompt writer:** the AI that writes and revises prompts.
- **Prompt reviewer:** a separate AI instance that reviews each prompt before it's used.
- **Paper reviewer:** the final prompt, run in a fresh session on the materials.

## Files

| File | What it is |
| --- | --- |
| [`1-first-draft.md`](1-first-draft.md) | My first prompt, written in about 15 minutes, with its known flaws |
| [`2-final-prompt.md`](2-final-prompt.md) | The same prompt after two rounds of review: it asks the prompt writer to write the paper reviewer |
| [`3-paper-reviewer.md`](3-paper-reviewer.md) | The generated paper reviewer, adapted for the test and run as written |
| [`4-test-setup.md`](4-test-setup.md) | How the materials were gathered and the test was run |

## What the test does and doesn't show

Asked to review a sample (the main theorem, then Lemmas 8.7 and 8.6), the paper reviewer found the known mismatch in Lemma 8.6, where the paper claims four extra derivatives and the Lean proves the estimate with five. It also flagged issues the critique doesn't mention.

- It was pointed at a lemma the critique had flagged, alongside a control lemma. It wasn't told which was which, or that an error existed.
- It read the Lean source but didn't build or run it.
- Its other findings haven't been independently verified.
- Passing this test doesn't guarantee a review catches every error.

## Sources

- Bastounis, Circelli and Hansen, ["Navier–Stokes Lost in Translation"](https://arxiv.org/abs/2610.08144)
- OpenAI, ["On the Navier–Stokes Millennium Prize Problem"](https://openai.com/index/navier-stokes-solution/)
- OpenAI's Lean repository at [commit f9e8bc5](https://github.com/openai/NavierStokesAndEuler/tree/f9e8bc5)
