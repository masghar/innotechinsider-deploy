# Anthropic Claude Formally Verifies Fermat’s Last Theorem

> Anthropic has completed the formal verification of Andrew Wiles’s Fermat’s Last Theorem proof in Lean 4, marking a historic leap for AI in pure mathematics.

By InnotechInsider Staff · New AI Models · Sep 5, 2026
Canonical URL: https://innotechinsider.com/ai-models/anthropic-claude-formalizes-fermats-last-theorem-lean4/

> **TL;DR** Anthropic has successfully used an autonomous, multi-agent implementation of Claude to translate and formally verify Sir Andrew Wiles’s entire 1995 proof of Fermat’s Last Theorem into the Lean 4 interactive proof assistant, shaving years off human estimates.

For more than three centuries, Fermat’s Last Theorem was the most famous taunt in mathematical history. Pierre de Fermat scribbled in the margin of his copy of Diophantus’s *Arithmetica* in 1637 that he had discovered a truly marvelous proof that $a^n + b^n = c^n$ has no whole-number solutions for $n > 2$, but that the margin was too narrow to contain it.

When British mathematician Sir Andrew Wiles finally conquered the problem in 1994—after seven years of secret toil and an agonizing peer-review correction published in 1995 alongside Richard Taylor—the proof spanned over a hundred pages of formidable, bleeding-edge 20th-century machinery: elliptic curves, modular forms, Galois representations, and the Taniyama-Shimura conjecture. It was universally accepted by human experts, but it remained out of reach of mechanized verification.

Until today. This morning, Anthropic announced that a specialized neuro-symbolic pipeline powered by its Claude model family has closed the final lemma in the formalization of Wiles’s proof, synthesizing the entire landmark achievement into machine-checkable code in [Lean 4](https://lean-lang.org/).

What top academic consortia had projected would take a dedicated community of mathematicians until at least 2030 has been fully verified in the early autumn of 2026.

## The 30-Year Mountain Meets Machine Verification

Formalizing modern mathematics is notoriously brutal. When mathematicians read a paper, they glide over phrases like "by standard properties of automorphic forms" or "it easily follows that." These semantic leaps save human readers hundreds of tedious hours, but to a rigorous computer verification kernel, they are unforgivable chasms.

![computer programmer typing lean proof assistant code on dual monitor setup](https://images.pexels.com/photos/16129724/pexels-photo-16129724.jpeg?auto=compress&cs=tinysrgb&fit=crop&h=627&w=1200 "computer programmer typing lean proof assistant code on dual monitor setup — Photo by Lisa Fotios on Pexels")

A computer does not accept hand-waving. Every object, from the definition of a scheme to the intricate behavior of deformation rings, must be derived from bedrock axiomatic foundations like Zermelo-Fraenkel set theory with the Axiom of Choice.

Formalizing Wiles’s work on [Fermat's Last Theorem](https://en.wikipedia.org/wiki/Fermat%27s_Last_Theorem) became a grand challenge in the late 2010s and early 2020s. Mathematicians like Kevin Buzzard at Imperial College London launched coordinated initiatives to build the necessary machinery in Lean’s Mathlib, a sprawling community library of formalized mathematics. Yet the progress was painstaking. While foundational layers were gradually added, full formalization remained a massive engineering grind requiring dozens of human work-years.

Anthropic’s announcement upends that timeline entirely. Working in conjunction with leading academic formalizers, Anthropic deployed an orchestrated cluster of reasoning agents that parsed mathematical prose, cross-referenced literature dependencies, and generated syntactically rigorous Lean 4 code. The breakthrough demonstrates how advances in [ai models](/ai-models/) are pivoting away from probabilistic text completion and toward rigorous, zero-hallucination symbolic environments.

## How the Proof Was Conquered

The fundamental weakness of large language models in higher mathematics has always been their tendency to hallucinate plausible-sounding nonsense. If an LLM tells a layperson an equation balances, the layperson might believe it; if it tells Lean 4 an equation balances, the Lean compiler throws a diagnostic error and halts execution.

Anthropic turned that unforgiving strictness into an evolutionary advantage. Instead of relying on a single model run, the company built a recursive architecture called "AutoFormalizer-Loop." Claude was not merely guessing Lean tactics; it was situated in an active read-eval-print loop with the Lean 4 compiler, using compiler error traces to prune invalid logical branches in real time.

| Pipeline Metric | Human-Led Verification (Historical Est.) | Claude Lean 4 Verification Pipeline |
|---|---|---|
| **Total Timeline** | 6–8 years (est. completion ~2030) | 11 months (completed Sept 2026) |
| **Lines of Formal Code** | ~3.8M projected | 4.12M verified Lean 4 lines |
| **Tactic Repair Rate** | Manual (hours/days per lemma) | 88.4% autonomous repair on first error pass |
| **Verification Basis** | Human-translated Mathlib lemmas | Hybrid: Human blueprint + Claude tactic search |
| **Soundness Engine** | Lean 4 Microkernel | Lean 4 Microkernel (Deterministic) |

The pipeline separated the formalization process into three concurrent tiers:

1. **The Blueprint Deconstructor:** An architectural agent ingested the prose papers—specifically Wiles’s 1995 paper "Modular elliptic curves and Fermat's Last Theorem" and the Taylor-Wiles paper on ring-theoretic properties—mapping them into a directed acyclic graph (DAG) of intermediate lemmas.
2. **The Tactic Synthesizer:** Sub-agents specialized in specific branches of algebra and geometry (such as Hecke algebras and Selmer groups) tackled individual nodes of the DAG, translating high-level mathematical argumentation into explicit Lean 4 `tactic` blocks.
3. **The Microkernel Arbiter:** Every output was fed straight into the native Lean kernel. If Lean accepted the proof, the node was marked green and frozen. If Lean rejected it, the diagnostic log was fed back into the tactic synthesizer for prompt-chain debugging.

Crucially, the microkernel does not know or care that an AI generated the code. The proof either type-checks or it does not. In Lean, an accepted proof is a mathematical certainty, entirely insulated from hallucination.

## Bridging the "Semantic Abyss"

The hardest part of the project was not the final calculation, but what formalizers call the "semantic abyss": bridging 19th-century classical analysis with mid-20th-century Grothendieck-style algebraic geometry.

To prove Fermat’s Last Theorem, Wiles had to prove a semistable case of the modularity conjecture (now the [modularity theorem](https://en.wikipedia.org/wiki/Modularity_theorem)), which asserts that rational elliptic curves are related to modular forms. Translating those concepts required establishing an immense scaffold of scheme theory in Lean—an effort that often stalled human teams simply because writing out tens of thousands of basic structural definitions is utterly exhausting for human researchers.

Claude excelled at this exact type of high-context, repetitive structural scaffolding. When human formalizers hit a roadblock, it was often due to obscure type-mismatch errors across imported libraries. Claude’s vast context window allowed it to ingest entire sub-libraries of Mathlib, identify signature mismatches, and synthesize the missing glue code in seconds.

The broader implications for [science](/science/) extend far beyond algebraic number theory. The exact same pipeline that bridges Wiles's intuitive mathematical jumps can be applied to complex physical simulations, biochemical kinetics, and formal proofs of chemical equilibria, changing how scientific consensus is reached.

![server room corridor with glowing blue led lights in a modern data center](https://images.pexels.com/photos/1148820/pexels-photo-1148820.jpeg?auto=compress&cs=tinysrgb&fit=crop&h=627&w=1200 "server room corridor with glowing blue led lights in a modern data center — Photo by panumas nikhomkhai on Pexels")

## The Trust Paradox: When Humans Can’t Read the Solution

Anthropic’s milestone creates an extraordinary intellectual paradox: we now possess an indisputable, verified artifact of Fermat’s Last Theorem that almost no single human being can fully read from top to bottom.

At 4.12 million lines of Lean 4 code, the formal proof is vastly larger than the English-language original. It is an intricate, monolithic program. Yet paradoxically, it is *more* trustworthy than the text that human mathematicians reviewed over the course of months in 1994 and 1995. Human review is susceptible to fatigue, social deference, and shared cognitive blind spots. The Lean kernel is not.

This dynamic is rapidly transforming high-stakes engineering disciplines. In areas like hardware verification and [future tech](/future-tech/) architectures, formal methods have historically been abandoned because the overhead of writing formal specifications was too high. If models like Claude can automate the translation from high-level architectural intent to verified machine proofs, zero-bug software and provably secure cryptographic implementations become standard realities rather than academic fantasies.

## The New Era of the Mathematical Co-Pilot

The mathematical community’s reaction this morning has ranged from sheer elation to quiet, existential vertigo.

There was a long-standing belief among purists that pure mathematics would remain a sanctuary from generative models—that while an LLM might write boilerplate JavaScript or summarize a quarterly earnings call, the sublime architecture of modern arithmetic geometry required an intuitive spark that tokens simply could not capture.

Anthropic’s achievement proves that AI does not need to possess human intuition to conquer human summits. By pairing generative fluency with the deterministic discipline of a formal verification engine, Claude did not "solve" Fermat’s Last Theorem through brute-force imitation; it painstakingly paved every millimeter of the road that Wiles had blazed with human genius.

Fermat once wrote that his margin was too narrow to hold his proof. Three hundred and eighty-nine years later, Anthropic found a margin large enough: a Lean 4 repository spanning four million lines of formal logic, sealed forever by a compiler that never blinks.
