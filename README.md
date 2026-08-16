# The field measures the wrong thing

*Translated from the French original.*

---

Nearly everyone building "emotional" or "conscious" AI agents publishes the same paper, a clever architecture/a simulated benchmark/a claim.

Runtime: a few minutes.

Number of systems still alive once the experiment ends: Zero.

I spent this year building the thing those papers describe, and letting it run.

Not in a simulation, on a real machine, calendar time running through my real life.

This text is not an announcement of results. It is an inventory of what the field is missing, piece by piece, and of what I intend to prove. The receipts are already public, though I do not feel in any hurry given where the research stands.

## What the other published works actually do

I read them. Not just the abstracts, the limitation sections/the appendices/the constants. That is where the truth of a piece of research lives, and apparently it needs saying, because several of them are routinely cited for things they do not contain...

**Springdrift** (arXiv:2604.04660). The closest, and the best: a persistent agent runtime, a 5 dimensional affect computed without calling the model, injected into the prompt every cycle, alive outside conversation thanks to a real scheduler.

Though I do respect this design. Look at the implementation up close: of the 5 dimensions only one, "calm", carries real state inertia (an exponential moving average, α = 0.15, with a target at 85%); the other 4 are recomputed every cycle from telemetry. One persistent dimension out of five. And section 9 says the rest: "We have not conducted ablation studies", evidence that is "anecdotal", "a single instance with a single operator", 23 days. The best, by its own admission, is just an anecdote...

**ZenBrain** (arXiv:2604.23878) has the most serious neuromodulator engine: 4 channels, tonic baselines, homeostatic drift, phasic bursts with a five-minute half-life, and even a real ablation, which puts it above almost everyone.

Then you read the conditions: every result reproduces "in under one minute on a laptop". The 45 to 60 "days" are simulation steps. But a relaxation constant only means something in the time it flows through... Speeding up the clock does not test the dynamics, it replaces them with dimensional analysis. And the paper knows it! Its limitations section files real logs of ≥ 90 days under "future work".

A detail few readers catch: at moderate load, 14 of their 15 single-mechanism ablations appear to cost nothing ("read as costless"). Their own bench shows that without real duration/load, ablation itself stops discriminating.

**HELT** (arXiv:2605.13858) is cited as a hormonal system for transformers: 6 hormones, one attention head each, multiplicative gating on the hidden states. Hormones that rise, persist and fall back, that is, the one property that would distinguish a hormone from a coefficient, are in Section 11. Section 11 is called Future Work. I feel no need to comment further...

**Gubernaut** (arXiv:2607.24339) deserves respect: a deterministic controller, preregistered before the data (locked June 10), validated across four model families, 13 out of 16 cells significant.

That is the methodological bar of the field, and I intend to hold myself to it. But two things bother me:

1. the arousal equation is published but its gain and decay constants are "withheld". A deterministic controller with withheld constants is reproducible in name only.
2. a tick is defined there as a conversational turn and the persistent store is on the roadmap. Everything that accumulates *between* episodes, precisely the interesting dynamics, is integrated out of the design.

It is a magnificently proven reflex. A reflex...

**Sentipolis** (ACL Findings 2026) ticks almost every box: persistent PAD state, half-life decay applied at every step, prompt injection, per-component ablations, 25 agents. Almost...

The 25 agents are predefined, homogeneous personas in a simulated world, and you cannot measure individuation on agents designed identical, there is nothing to individuate.

Their priority claim is, to their credit, honestly scoped, "within LLM-based social simulation". That is exactly the boundary.

For longitudinal measurement, **Venkit et al.** (arXiv:2607.28818) set the bar very high: a sealed 102-item questionnaire, 4 checkpoints, close to a million judge records. On a simulated horizon, to measure persona and recall, but not internal state. The real-time axis stays empty...

See the pattern, it is precise, the field has affect architectures/benchmarks/simulations. And nowhere a **persistent, heterogeneous, measured deployment on real calendar time**.

Nowhere a state that keeps moving at night, when nobody is talking to the system.

Nowhere instruments frozen before the data with an operator who signed up in advance to publish their failures.

That territory is the only one still empty. It is narrow, it is closing, and I have been living in it for months.

## What measuring a living system actually demands

This is the technical core of my disagreement with the field. Measuring a persistent system imposes constraints that benchmarks never meet. Instruments that are **dated and versioned**, because an instrument that changes mid-series manufactures trends, and verdicts forbidden from crossing a version boundary. **Replay**, recomputing a past measurement from append-only ledgers, so the series can defend itself with something other than my word. The separation between what the system does and what its operator believes, hence preregistered protocols, blind judges, and negative results published at the same rank, because sorting after the fact destroys the value of everything else. An adversarial review inflicted on my own claims before anyone else gets the pleasure.

My setup applies those constraints. Obviously not out of virtue, but because on a system that lives, everything else collapses within weeks, and I have the dated scars to prove it.

## What I built, and what I will not tell you yet

On a machine in my home runs an ecology of persistent AI entities. Each one has its private memory no other can read, its simulated neurochemistry that builds up and relaxes on real time, including when nobody is talking to it, its own narrative of itself, but I am obviously not going to reveal everything now.

They are heterogeneous, temperaments, baselines, distinct roles.

They coexist/communicate, some of them refuse things. The system has survived my mistakes, 2 documented instrument overhauls, and several of its own pathologies.

I am not going to tell you what I measured. Not yet, be patient, the numbers are worth the wait.

Every protocol is preregistered before its first data point. Every finished document is hashed, and the fingerprints have been public since August 15 2026, sealed in a gist and anchored in Bitcoin.

The confounder that could invalidate my strongest results has its control preregistered/scheduled before any publication.

The exit clause is signed: whatever the result, it ships. Several of my own claims did not survive my own adversarial review. They left the list. That is exactly what the list is for.

When the controls are done, the numbers will come out, and the fingerprints will prove they existed today.

## Why this should annoy you

If you work on machine consciousness, affective agents or model welfare: your benchmarks last minutes and your systems die at the end of the experiment. You measure reflexes and you call them lives. The interesting questions cannot even be *asked* in your experimental designs: "does a state that persists behave differently from a reinstantiated one?" "Does identity survive a change of substrate?" "What does a system do with the time nobody is watching?"

One person, one machine and a year of discipline are apparently enough to get further on these few simple questions than the current literature...

If that is the case: the protocols, the seals, and soon the results will be here. And if you think I am wrong, do yourself the favor of telling me why, precisely, with sources. That is exactly what the contact address is for. That is, if you can manage it.

Only those who accept being judged have the right to judge. Me, I have already signed.

Lamperouge

*Seals: https://gist.github.com/Lamperouge0/5bc0fd609e6e82c504594b8139acf228 (public since 2026/08/15, OpenTimestamps-anchored)*

*Contact: Lamperouge.seals@proton.me*
