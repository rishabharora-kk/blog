---
title: "Verification Is the Binding Constraint"
subtitle: "Fluency with a tool stops predicting competence at the task, and the gap does not close with experience"
section: essays
date: 2026-09-14 09:00:00 +0530
summary: >-
  Skill does not increase without a cost for being wrong. Frontier labs pay a
  6x spread inside one company for work that resists specification, which is a
  premium on verification rather than on production. One metric detects whether
  a working day generated any learning at all.
---

An operator's value is bounded above by their capacity to verify their tools' output. Below that bound, a more powerful tool amplifies errors at exactly the rate it amplifies successes, and the expected gain from an arbitrarily strong generator is zero.

That bound is not obvious from inside, because the instrument people use to check it — the felt sense of moving fast — has been measured, and it is inverted.

<nav class="toc" markdown="1">
#### Contents
{:.no_toc}
* placeholder
{:toc}
</nav>

## The two obvious answers

There are two default responses to someone who has gone fluent with AI tools and stopped improving. This argument rejects both, so they are worth stating first, at their strongest.

**One:** the deficit is unassisted production, so the remedy is to stop leaning on the tools and practise by hand until production returns. **Two:** pay at frontier labs tracks seniority and the difficulty of the labour, so the spread inside a company should be modest and the top of the band is mostly a reward for tenure.

Both are checkable against public data. Both fail, and they fail in the same direction.

## What the frontier prices

Reported figures, from compensation aggregators and public filings. Treat them as order-of-magnitude rather than precise, and check the links at the end.

- Anthropic's reported band runs from roughly **$199K** total compensation at the low end (Trust and Safety) to about **$1.27M** at the high end (staff-level software engineer). Federal H-1B filings reported base salaries of **$1.12M–$1.38M** for people titled *Member of Technical Staff* — base cash, before equity.[^anthropic-comp]
- OpenAI: Research Scientist total compensation reported around **$763K (L4) to ~$1.39M (L5)**, median package around **$1.25M**; base bands for Member of Technical Staff (Research) around **$245K–$685K**. Senior retention grants have been reported in the **$5M–$20M/yr** range.[^openai-comp]
- Both converge on the same title architecture — *Member of Technical Staff*, *Research Engineer*, *Research Scientist* — with engineering and research on one ladder.

The top number is the least informative part. The signal is the **ratio**: roughly 6x between the low and high band inside a single company. A spread that wide is not tracking seniority, and it is not tracking how hard the labor is. It tracks **irreducibility** — how badly the work resists being specified in advance.

The cheap end of the band is work that can be described before it is done. The expensive end is work where nobody yet knows what a correct answer looks like: alignment, interpretability, frontier training, reinforcement learning, large systems failing in novel ways. The premium is not on coding. It is on **formulating and verifying** where there is no specification and no oracle.

### What they say they select on

From Anthropic's careers page:

> "We care about what you can do, not where you learned to do it. About half our technical staff had no prior ML experience; about half have PhDs, but plenty of brilliant colleagues never went to college. **If you've done interesting independent research, written a thoughtful blog post, or contributed to open source, put that at the top of your resume.**"[^anthropic-careers]

> "Engineers here do lots of research, and researchers do lots of engineering... All our papers have engineers as authors, often as first author."[^anthropic-careers]

From a Research Engineer / Alignment posting, under *Candidates need not have*:

> "100% of the skills needed to perform the job. Formal certifications or education credentials."[^anthropic-re-alignment]

The *good fit* list from that posting, in its order: significant software, ML, or research engineering experience; contributing to empirical AI research; familiarity with technical AI safety research; prefers fast-moving collaborative projects to extensive solo efforts; picks up slack even if it goes outside the job description; cares about the impacts of AI.[^anthropic-re-alignment]

From OpenAI's Research Engineer page:

> "We're looking for people with solid engineering skills (for example designing, implementing, and improving a massive-scale distributed machine learning system), writing bug-free machine learning code, and building the science behind the algorithms employed... engineers who are comfortable working in large distributed systems."[^openai-re]

### Decoding the postings

Job-post prose, translated into the capability being purchased. This column is inference, not data — the quotes above are the data.

| Stated requirement | Capability being bought |
|---|---|
| "design and run elegant, thorough experiments" | Converts a vague intuition into a test that could come out either way, and knows which outcome would refute it |
| "understand why systems behave as they do" | Holds a causal model of an opaque system; debugs by hypothesis, not by mutation |
| "writing bug-free ML code" | Has an internal error model — knows where bugs live before they manifest |
| "massive-scale distributed systems", "complex shared codebases" | Reasons about systems larger than working memory |
| "papers have engineers as first author" | Can write. Prose quality is a readout of thought quality, and it is being selected on |
| "picks up slack outside the job description" | Agency without a specification |
| "no credentials required; put independent research at the top" | Artifacts are the currency; credentials are an explicitly discounted fallback |

**Interview gates are gates, not the game.** Data structures and live coding are not a typing test and not a proxy for productivity. They are an unplugged verifier test: with the oracle removed, is there an internal model of the machine, and can a system be held in working memory and reasoned about? That is why hand-writing code is the measurement instrument — it is the only way to observe from outside whether the internal model exists. It is a floor, not a ceiling, and clearing a pass/fail gate cheaply is correct strategy rather than something to resent. It is also not where the compensation is.[^interview-gate]

**The trajectory points at verification.** Anthropic has reported evaluating whether a model's proposed next experimental step beats the human researcher's, and states it reaches parity in a substantial fraction of real research sessions.[^anthropic-rsi] Generation of research *steps* is being absorbed. What stays scarce inside the lab is what is scarce in any individual workflow: someone who can tell whether the machine's output is right, and who decides what should be attempted at all.

## Three absences, and why the innermost one is invisible

Stagnation inside a high-activity workflow is not a defect in what is present. It is a missing mechanism — and three go missing together, nested, the outer ones cheap and visible, the inner ones load-bearing.

### Recognition is not production

Reading correct code and producing it are distinct capacities. Recognition is cued retrieval against a stored trace; production is free recall plus construction. Recognition is systematically easier, and it is the standard source of overconfidence, because the phenomenology of *yes, that's right* is nearly identical to the phenomenology of *I could have written that*. It is possible to read a language one cannot speak.

The consequence is a working ceiling equal to the model's ceiling, with the operator's judgment contributing nothing.[^skill-atrophy] In a market where everyone holds the same model, that is a commodity position with no growth term.

### The instrument is broken, which hides the first absence

The brain uses **fluency as a heuristic cue for understanding**. Information that arrives smoothly is judged better-understood than information that arrives with effort, independent of actual comprehension. AI output is maximally fluent, so it maximally triggers the false cue. This is the machinery behind the illusion of explanatory depth — people confidently report understanding how a bicycle or a zipper works until asked to draw one.[^unsourced-fluency]

The industrial-scale version is the part worth internalizing precisely. In METR's randomized controlled trial, experienced open-source developers working on real tasks in their own repositories were **19% slower** with frontier AI tools. They had forecast a 24% speedup beforehand. Afterwards — having personally lived through the slowdown — they estimated they had been sped up by **20%**. The belief survived direct experience of the opposite.[^metr]

The structure of that result matters more than the headline. It does not show that AI does not help; METR was explicit on that point, and different tasks, workflows, and models can and do differ. The transferable finding is narrower and less comfortable: **the subjective sense of speed is not a measurement of speed, and it does not correct itself through experience.** The feeling is generated by the smoothness of the interaction, not by the throughput.[^perception-gap]

The name for the surrounding state is **metacognitive laziness**: fluent answers remove the difficulty signals that normally trigger self-monitoring, so verification stops being invoked at all. Anyone citing a feeling of efficiency as evidence that their method works is citing the one reading they are not licensed to trust.[^metacog-laziness]

### There is no loss function

Learning requires an error signal with teeth. There are three sources of teeth: reality breaks something, other people judge it, or a prior commitment is contradicted. A tool-saturated solo workflow removes all three.

- **Reality.** The tool patches over gaps before they manifest as failures, so not knowing costs nothing locally. The bill is deferred and accrues as *cognitive debt* — code produced faster than comprehension of it, until no one can say what the program does or how to change it safely.[^cognitive-debt]
- **Other people.** Nothing made is exposed to anyone with standing to call it bad.
- **Commitment.** Nothing is predicted before it is observed, so nothing can be surprising — and surprise is the only free source of labels.

The result is not a small gradient. It is zero gradient. Years of activity with no shaping pressure produce exactly enthusiasm, breadth, fluency, and no movement. The system is behaving correctly given its inputs.

**Skill is a function of consequence density.** There is no known mechanism by which competence increases in the absence of a cost for being wrong. A frictionless environment does not shape anyone, however sophisticated it looks from inside.

## Boredom is a correct measurement pointed at the wrong variable

Two claims, both true, and the tension between them is where the leverage is.

**The boredom is accurate.** Tutorials and structured courses are genuinely low-value, and not because the learner is too advanced. It is structural: a tutorial is a guided path with no possibility of failure. It is engineered so the learner cannot be wrong, which means it cannot generate a single labeled error. It produces the sensation of learning — fluency, progress bars, working output — with near-zero information transfer. The boredom is detecting a real absence.

**The boredom misattributes the cause.** The conclusion usually drawn is *manual practice is redundant*. The supported reading is *instruction-following is redundant*. These feel identical from inside and are opposite in consequence. What made tutorials dead was the absence of falsification — and the absence of falsification is also what characterizes tool-saturated work. The common move is to flee one zero-feedback environment into a second zero-feedback environment with better aesthetics. That is why the stagnation follows.

The underlying mechanism says which lever works. Dopaminergic signalling encodes **reward prediction error** — the difference between expectation and outcome — not reward magnitude. Applied to learning, the operative quantity is *learning progress*: the rate of change of competence, not its level. Intrinsically-motivated agents built on this principle abandon a task the moment the derivative flattens, regardless of the absolute value of the skill. This is the standard architecture of curiosity-driven learning and a well-documented account of human boredom.[^unsourced-rpe]

Which means the problem is not insufficient discipline, and resolve will not fix it. Resolve does not change a reward schedule; it spends finite willpower fighting one, a losing trade on any horizon longer than a few weeks. The intervention has to change the **information geometry of the task** so that the derivative of *visible* competence stays high.

Three calibration points, because the reverse error is available and real.

**Difficulty must be desirable, not merely present.** Difficulty aids long-term retention while hurting short-term performance — generation over reading, testing over review, varied over blocked practice.[^bjork] But this reverses when working memory is already saturated: with high element-interactivity material and no scaffolding, added difficulty is *undesirable* and produces load and nothing else.[^undesirable-difficulty] The target is the region where failure happens roughly a third of the time — enough to generate signal, not so much that the signal is noise.

**AI output is a worked example, which is the right scaffold at the wrong moment.** For a genuine novice, a complete worked solution beats problem-solving; that is the worked-example effect, and it means the intuition that AI-assisted work teaches *something* is not baseless.[^worked-example] But the effect reverses with expertise, and a *complete* example is inferior to an **incomplete** one. Examples with steps deliberately removed, which the learner must supply, produce better self-explanation and better transfer.[^worked-example] That is the whole fix, stated technically: do not stop using worked examples — delete parts of them before reading, and supply the deletions.

**Surprise is the fuel.** The highest-density source of reward prediction error available to a learner is being wrong about something just committed to. Prediction-before-observation converts every observation into a labeled error signal. It manufactures consequence out of nothing, generates the surprise that *is* the reward being chased, and measures calibration as a free side effect. It also restores the structure boredom needs: a game has an opponent and a scoreboard, and prediction supplies both.

So the apparent dilemma between speed and depth is not a dilemma. The move is to **insert a prediction between the request and the answer**. It costs seconds and converts the workflow from consumption into training.

## The waterline

Capability commoditizes from the bottom of the abstraction stack upward. Each layer, once machine-cheap, stops paying.

```
   owning the consequence        <- not automatable: requires a self with skin
   judgment under irreducible
     uncertainty                 <- the compensation premium lives here
   problem formulation           <- "what is even the right question"
   problem selection / taste     <- being actively measured, contested
-- waterline, moving up --------------------------
   architecture                  <- falling now
   implementation                <- mostly gone
   syntax / recall of APIs       <- gone
```

The intuition that hand-writing code is a bad investment is **correct about the bottom three layers**. It is a sound read of the trajectory. The error is concluding there is therefore nothing to invest in. There is; it sits above the waterline, and it is reachable by neither the tutorial route nor the pure-delegation route.

This is also what happens as models improve. The scarce complement to a stronger generator is never a better generator — it is a better **discriminator**. Generation is being supplied at collapsing marginal cost. Discrimination is not. The 6x compensation ratio, the job-post language about knowing *why* systems behave as they do, and labs measuring research taste because it is the remaining bottleneck all point the same way.[^taste]

### Why the discriminator requires having been a generator

Here is the part that dissolves the tradeoff:

> **A discriminator cannot be trained without generation. You have to have built the thing to know how it breaks.**

An error model — the intuition that says *this looks wrong* before it can be articulated — is compiled out of one's own failures, in one's own hands, with one's own bugs. It cannot be installed by reading, transferred by explanation, or borrowed from the model. It is the residue of having been wrong in a specific way often enough that the shape became recognizable. There is no shortcut, and the absence of a shortcut is good news: this capability does not commoditize.

Which licenses the reclassification the whole argument turns on:

**Hand-writing code is not production. It is instrumentation.**

The point is not to obtain the code; at that the machine wins and will keep winning. The point is to **calibrate a detector**, and the detector is the asset — the thing still worth something in five years, the thing the interview is probing, and the thing the top of the band is paying for. A calibration weight is not useful for building houses. That was never the objection to it.

## The metric

The highest-leverage intervention in a system is rarely the effort parameter. It is the information flow, and what gets measured.

> ### Maximize **labeled errors per unit time.**
> A *labeled error* is an occasion on which a specific expectation was committed to, and reality returned a verdict that could not be argued with.

The usual options sort themselves against it without further argument.

| Activity | Labeled errors/hour | Why |
|---|---|---|
| Watching a tutorial | ~0 | Engineered so the learner cannot be wrong |
| Reading documentation | ~0 | No commitment, so no verdict |
| AI writes it, skim, it runs | ~0 | The model absorbs the errors; yours never surface |
| AI writes it, skim, it breaks, AI fixes it | ~0 | Still the model's error signal, not the operator's |
| Predict output, run, diff | **very high** | Every line is a labeled trial, seconds per cycle |
| Write from a blank file against a test suite | **high** | The failures are yours, the verdicts mechanical |
| Predict the tool's approach before asking, then diff | **high** | Free, continuous, fits an existing workflow |
| Ship something people use | **high, and unfakeable** | Reality supplies labels nobody would think to request |
| Publish reasoning where competent people can see it | **high** | Others find the errors one's own model is blind to by construction |

Four properties carry the weight.

1. **It resists Goodhart.** Gaming it requires doing the work. Prediction accuracy on unseen code cannot be inflated without actually modelling the system. Compare lines written, hours studied, repositories starred — all trivially gameable, which is why they are the metrics people reach for.
2. **It reframes failure as yield.** A day full of being wrong is a high-output day. That inverts the emotional sign of the obstacle, which is usually not laziness but aversion to visible incompetence.
3. **It restores the derivative.** Labeled errors per hour is high-frequency, visible, and trends. It supplies a fast progress signal from a source that is real rather than illusory, which is why it does not require discipline to sustain.
4. **It is a defensible target for pride.** Not *I use AI well* — a tool choice, and tools change underneath. Not *I know N languages* — unfalsifiable. Instead: *my predictions about systems are calibrated, and I can tell when output is wrong.* That claim is testable, and it is what the top of the band buys.

The corollary is the single most useful question to ask about any activity: **what would tell me I was wrong, and how fast?** With no answer, the activity is entertainment. That is allowed. It should not be scored as growth.

## Four loops

Loops, not steps. Each has a verdict mechanism the practitioner cannot author, and each is instrumented so the derivative of competence is visible — the only thing that keeps anyone in the loop. None of them requires giving up the tool.

### 1. Interception — daily, nearly free, the keystone

Before asking the model for anything non-trivial, write down — in a file, not in your head, because unwritten predictions are retroactively edited — the approach you would take, the shape of the solution, the part you expect to be hard, and the specific place you expect a bug.

Then ask. Then **diff the prediction against the answer**, and log one line: where it matched, where it differed, and — separately, this distinction is the point — whether the difference was an error or merely a different valid choice.

It costs under a minute. It converts an unlimited supply of fluent worked examples into an unlimited supply of labeled trials, rides a workflow already run dozens of times a day, and is a direct calibration measurement. Ten interceptions a day is roughly 3,000 labeled trials a year against a frontier model.

*Instrumentation:* weekly match rate. When it climbs, judgment is converging on the model's. When it plateaus high, start predicting where the *model* is wrong, and check. That is the graduation.

### 2. Deletion practice — three or four times a week, 30–45 minutes, bounded on purpose

Take something the tool built recently and that you understand in the recognition sense. Delete a functional piece. Reconstruct it from a blank file, against the existing tests, with the model closed.

Start with deletions small enough to succeed about two times in three. Grow the deletion until that ratio holds again.

This is the incomplete-worked-example effect: generation rather than review, which is the strongest desirable difficulty, scoped so working memory is not saturated, which is what keeps the difficulty desirable rather than merely painful.[^generation-effect] The verdict is mechanical and instant.

*Instrumentation:* deletion size reliably restorable, and time to restore. Both are numbers and both move weekly. This is the loop that puts a visible derivative on the missing capability — precisely what was absent when tutorials went flat.

Hard rule: time-boxed. This is calibration, not production. It is supposed to end.

### 3. The artifact — continuous, and the actual deliverable

One real project, chosen on three criteria in priority order:

1. **Free verdicts.** Success and failure are decided by something other than the author's opinion — a number replicates or it does not, a test passes or it does not, a user returns or does not.
2. **High ceiling.** It absorbs ten years of increasing sophistication without changing identity.
3. **Overlap with what is priced.** Empirical work on systems nobody fully understands.

Two shapes satisfy all three unusually well. **Reproduce a published mechanistic-interpretability result on a small model, then extend it by one question of your own** — verdicts are free, the extension is where judgment enters and becomes visible, the ceiling is unbounded, and it lands exactly on "interesting independent research." Or **build and publish an evaluation for a capability nobody has measured well** — eval-writing *is* the discriminator skill turned into a product, the act of specifying what "correct" means where nobody has. It is in demand, legible, and achievable alone.

Use the tool at full throttle inside this. That is not cheating; it is the working condition of the job. One rule: **publish the reasoning, and own the claims.** A result whose grounds cannot be defended is a result that does not get stated.

*Instrumentation:* one public artifact per six weeks or so. Not a post *about* something — a thing you did, what you found, what you expected, and where you were wrong.

### 4. Exposure — every six weeks, minimum

Put the artifact in front of people with standing to judge it, in a venue where they are free to call it wrong. Not an audience. A jury.

It cannot be folded into the others, because an error model is blind exactly where it is broken, by construction. Only an external model finds those. This is also the entire mechanism of compounding, and the only loop that feels genuinely bad — which is the diagnostic that it is working, since it is the only one carrying real consequence.

**Interview gates**, separately: clear the data-structures and live-coding floor to a pass/fail standard, then stop. Treat it as a fixed cost paid efficiently, and do not let it become the thing done *instead of* an artifact — that substitution is comfortable, legible, and fatal, because it looks like progress while producing nothing. Loops 1 and 2 clear most of that gate as a side effect, which is not a coincidence: the gate is a verifier test, and those loops build the verifier.

**Under scarcity:** if only one loop is sustainable, run Interception — nearly free, rides existing habits, and it repairs calibration, which is what makes everything else steerable. If two, add the Artifact, because without one there is nothing to compound. Exposure is the one that gets dropped and the one with the highest marginal value. That asymmetry is not an accident; it is aversion doing its job.

## Where the exponential actually lives

**Skill is sigmoidal.** Within a domain, returns to practice follow a power law with a decelerating exponent: slow start, steep middle, plateau. Expecting exponential returns from this layer guarantees recurring disappointment — and that disappointment is itself a generator of boredom, because a sigmoid measured against an exponential expectation reads as failure of the method. It is not the method. It is the expectation applied to the wrong layer.

**Artifacts compound superlinearly.** The artifact layer is a network process, and network processes exhibit preferential attachment: each visible, verifiable piece of work raises the probability of the next opportunity, and opportunities beget visibility. Reputation is power-law distributed. Skill is not.

> **Growth rate is not set by learning rate. It is set by artifact rate multiplied by the verifiability of each artifact.**

Three consequences.

1. **Breadth without depth cannot compound.** Transfer happens from deep structure, never from surface familiarity. Ten shallow domains transfer nothing to an eleventh; one deep domain transfers to most. Breadth is not wasted, but it is not capital until one strand goes deep enough to generate transferable structure.
2. **An unpublished artifact has a multiplier of zero.** The quality of the work does not matter. Unexposed work generates no network effect and no external error-correction. Which is why Exposure is non-negotiable despite being the loop that gets skipped.
3. **The compounding layer and the hiring layer are the same layer.** Independent research, a thoughtful blog post, open-source contributions, at the top of the resume, credentials explicitly discounted — the thing that compounds *is* the thing that gets people hired. That convergence is rare and worth exploiting.

One concrete route: Anthropic runs a **Fellows Program**, with tracks including AI Safety and Security, ML Systems and Reinforcement Learning, and Economics and Policy — a structured entry that selects on demonstrated capability rather than credentials. They state they do not run internships, and permit re-application after 12 months.[^anthropic-fellows]

On distance, without encouragement: the gap between no shipped work and no published reasoning, on one side, and a frontier-lab research role on the other, is large, and it is measured in years of these loops rather than months. But the *shape* of the gap is favorable, and shape matters more than size. It is not credentialist, not political, and not gated behind anything that cannot be started today. It is a production gap, and production gaps close monotonically under a working loop. What is missing is one habit — the testing habit — and a habit is installable in a way a talent is not.

## How this fails

Named failure modes are catchable from inside while they happen. Unnamed ones are visible only in retrospect, which is too late.

**Meta-procrastination.** Reading a sharp analysis of a problem delivers the same fluency reward as solving it, at a fraction of the cost. This is the highest-probability failure by a wide margin, and the recursion is exact: an essay diagnosing an offloading habit is a perfect vehicle for it. *Detector:* 72 hours pass with nothing logged. *Countermeasure:* one interception today, before this feels complete. Feeling finished is the symptom.

**Converting loops into a curriculum.** Build a schedule, a tracker, a plan; feel the tutorial boredom arrive on cue; conclude the method failed. It did not — it was converted into the thing that fails. *Detector:* optimizing the system instead of running it. Building tooling for one's practice is procrastination in a lab coat.

**"Manual practice later, after this project."** It does not happen. Consequence-free environments do not spontaneously acquire consequence, and a project already running has no slot where difficulty naturally enters. The interception goes inside current work now, or not at all.

**Undesirable difficulty.** Overcorrecting — no tools at all, a project far beyond scope, a hard language from scratch. Working memory saturates, nothing is learned, and the result is a legitimate-seeming failure that generalizes into *I tried the manual thing, it doesn't work for me.* Stay in the two-of-three success band.

**Identity defense.** Pride attached to a tool choice generates motivated reasoning against all of this, and it arrives disguised as sophistication: *this overweights manual skill, the models will be better in a year, verification will be automated too.* Some of that is partly true, which is what makes it effective. *Detector:* arguing with the argument instead of running a loop. The argument may even be correct, and it is still, functionally, avoidance. A prediction match rate does not care about anyone's position.

**Goodharting the metric.** Logging easy predictions and scoring high. *Countermeasure:* the metric is labeled errors, not correct predictions. A week with a rising match rate on trivial predictions is a failing week. Predict the things you expect to get wrong.

**Fleeing at the plateau.** Deletion-practice numbers climb fast and then flatten, and the boredom instrument fires on schedule. What it measures is the derivative of *visible* competence, and the fix is to change the difficulty, not the domain. Domain-switching at the plateau is the exact behavior that produces a decade of breadth. It feels like curiosity. It is the plateau.

**Publishing polish instead of process.** Wanting the artifact to look impressive means hiding the errors, which removes the only part with value — and specifically the part the labs are reading for. A strong research submission reads like a methods section: precise, honest, explicit about what the work does and does not show.

## Where this is most likely wrong

First, the three framings this argument had to reject. Each is more plausible than what replaced it, which is why they survive.

**Tool dependence is not the variable.** Inability to write code from a blank file reads like the bottleneck. It is an observable of the bottleneck. Hand someone unassisted production tomorrow, change nothing else, and they still stagnate — they still have no mechanism that reports when they are wrong. People leaning on these tools harder than average do compound fast, when they check. The variable separating the cases is verification, not autonomy.

**Pay tracking seniority.** It tracks irreducibility instead, and the 6x internal spread is what gives that away. Reading the top of the band — where attention naturally goes — hides it completely.

**The growth curve, on the wrong layer.** Skill acquisition read as exponential, with the shortfall read as failure of method. Skill is sigmoidal. The exponential is real and lives one layer up, in artifacts, which is a network process and not a practice curve.

Then the things this does not settle. First, the compensation figures are aggregator- and filing-derived, not audited; the 6x ratio is robust to a fair amount of noise in the individual numbers, but I have not verified any single figure against a payroll record. Second, METR's result is one trial, on experienced open-source developers, in repositories they already knew — the specific 19% does not transfer to other populations, and METR says so; what I am claiming transfers is the *direction of the perception gap*, which is a weaker and better-supported claim. Third, the strongest counterargument is the one in the identity-defense section: if verification itself is automated to a high standard, the scarce complement moves again, and the discriminator loses its premium. I think that is the right thing to watch, and I do not think the argument survives unchanged if it happens. What would refute this piece is a demonstration that operators who cannot verify output nonetheless capture the gains from stronger tools.

One disclosure about standing, because it changes how the second half should be read. This is an analysis of a mechanism, not a report from someone who has run these four loops to completion and measured the result. The loops are derived from the cited literature and from the structure of the argument. The empirical claims above carry sources; the loops carry only reasoning, and they should be read as a proposed protocol rather than a tested one.

## The method, with the domain stripped out

The moves, in reusable form.

1. **Demand the loss function.** What generates verdicts here, who authors them, and how fast do they arrive? No loss function means no learning, however much activity there is. Start here.
2. **Distrust the stated problem.** A self-reported bottleneck has already passed through the reporter's model, which is the thing under examination. The presenting complaint is evidence about the complainant's model, not about the system. Ask what would have to be true for the stated problem to be the real one.
3. **Look for the missing mechanism, not the present defect.** Absence is systematically harder to see than presence, which is how it survives years of introspection.
4. **Find the self-refuting evidence.** When an argument rests on a subjective measurement, go and find out whether that measurement is calibrated. This move is available far more often than it is used.
5. **Read the spread, not the level.** A 6x ratio inside one organization is a stronger signal than any absolute number, because it reveals what that organization treats as substitutable. Levels are noisy; ratios are structural.
6. **Project the commoditization frontier.** For any capability: which layer of the stack is this, where is the machine waterline, and which way is it moving? That converts *is X worth learning* — unanswerable — into a positional question with a defensible answer.
7. **Find the scarce complement.** When an input's cost collapses, value migrates to the new binding constraint. Do not ask what is valuable; ask what the newly-abundant thing now requires more of.
8. **Reclassify before you optimize.** A forced choice usually encodes a mislabeled category. Most dilemmas are classification errors.
9. **Collapse to one metric, then stress-test it against Goodhart.** If gaming the metric is easier than satisfying it, the metric is worse than nothing.
10. **Solve for sustainability at the mechanism level.** Any prescription requiring someone to want what they do not want will fail. Knowing *why* they do not want it is the design specification for one that does not need willpower.
11. **Pre-label the failure modes**, including your own motivated reasoning, which is the one you will not catch otherwise.

## One sentence

Optimizing unlabeled output rate produces fluency and no movement. Invert it — optimize labeled error rate, keep every tool, relocate pride from the tool to the detector, and publish the residue.

[^anthropic-comp]: *Anthropic Salaries* and related compensation write-ups. The reported $199K–$1.27M total-compensation band and the $1.12M–$1.38M H-1B base-salary filings. [levels.fyi](https://www.levels.fyi/companies/anthropic/salaries), [levels.fyi (SWE)](https://www.levels.fyi/companies/anthropic/salaries/software-engineer), [Metaintro](https://www.metaintro.com/blog/anthropic-1-3-million-ai-roles-salary-2026), [CTAIO](https://ctaio.dev/en/salary/anthropic-salary/)
[^openai-comp]: *OpenAI Salaries* and related compensation write-ups. The Research Scientist and Member of Technical Staff bands and the reported retention-grant range. [levels.fyi](https://www.levels.fyi/companies/openai/salaries), [JobsByCulture](https://jobsbyculture.com/blog/openai-compensation-2026), [CTAIO](https://ctaio.dev/en/salary/openai-salary/), [Entrepreneur](https://www.entrepreneur.com/business-news/how-much-openai-employees-make-salaries-685000)
[^anthropic-careers]: *Careers*, Anthropic. Source of the two block quotes on hiring for demonstrated ability over credentials and on engineers doing research. [anthropic.com/careers](https://www.anthropic.com/careers)
[^anthropic-re-alignment]: *Research Engineer / Scientist, Alignment*, Anthropic (Greenhouse). Source of the "candidates need not have" quote and the "good fit" list. [job-boards.greenhouse.io](https://job-boards.greenhouse.io/anthropic/jobs/4631822008)
[^openai-re]: *Research Engineer*, OpenAI. Source of the quoted description of the role. [openai.com/careers](https://openai.com/careers/research-engineer)
[^interview-gate]: Sundeep Teki, *Anthropic Research Engineer Interview 2026*. Account of the data-structures/live-coding interview process referenced in the discussion of interview gates. [sundeepteki.org](https://www.sundeepteki.org/advice/anthropic-research-engineer-interview-2026)
[^anthropic-rsi]: *When AI builds itself*, Anthropic. The claim that a model's proposed next experimental step reaches parity with a human researcher's in a substantial fraction of sessions. [anthropic.com/institute](https://www.anthropic.com/institute/recursive-self-improvement)
[^taste]: Wenbo Pan, *Taste Is the Next Capability AI Will Crack*. Discussion of research taste as the remaining, measured bottleneck. [wenbo.io](https://www.wenbo.io/blog/taste-scaling/)
[^skill-atrophy]: *The Skill Atrophy Trap*, TianPan.co, and *A Review of the Negative Effects of Digital Technology on Cognition* (arXiv). The claim that unassisted judgment stalls at a ceiling set by the tool rather than the operator. [tianpan.co](https://tianpan.co/blog/2026-04-19-skill-atrophy-ai-augmented-engineering), [arXiv](https://arxiv.org/pdf/2603.10025)
[^metr]: METR, *Measuring the Impact of Early-2025 AI on Experienced Open-Source Developer Productivity*, and *AI Coding Tools Made Developers 19% Slower*. The 19% slowdown, the 24% forecast and the 20% post-hoc estimate. [metr.org](https://metr.org/blog/2026-02-24-uplift-update/), [letsdatascience.com](https://letsdatascience.com/blog/developers-thought-ai-made-them-faster-the-data-said-otherwise)
[^perception-gap]: *The Vibe-Check Protocol: Quantifying Cognitive Offloading in AI Programming* and *Using Biometrics to Understand AI-Assisted Coding Performance and its Perception* (both arXiv). Evidence that perceived speed and measured speed diverge and do not converge with experience. [arXiv (Vibe-Check)](https://arxiv.org/pdf/2601.02410), [arXiv (Biometrics)](https://arxiv.org/pdf/2606.20598)
[^metacog-laziness]: **Approximate support.** The term is used here for a mechanism the cited paper describes rather than names. *Mitigating "Epistemic Debt" in Generative AI-Scaffolded Novice Programming using Metacognitive Scripts* (arXiv). Source for the term and mechanism of metacognitive laziness under fluent AI output. [arXiv](https://arxiv.org/html/2602.20206v2)
[^cognitive-debt]: **Approximate support.** A conceptual match rather than the paper's own terminology. *Mitigating "Epistemic Debt" in Generative AI-Scaffolded Novice Programming using Metacognitive Scripts* (arXiv) and *AI-overdependence and human cognitive decline* (ScienceDirect). Support for the cognitive-debt framing of comprehension deferred past the point of production. [arXiv](https://arxiv.org/html/2602.20206v2), [ScienceDirect](https://www.sciencedirect.com/science/article/pii/S2451958826001764)
[^bjork]: Metcalfe & Bjork, *Desirable Difficulties and Studying in the Region of Proximal Learning*. The retention-vs-performance tradeoff across generation, testing and varied practice. [columbia.edu](https://www.columbia.edu/cu/psychology/metcalfe/PDFs/Metcalfe-BjorkVolSubmitFeb14Final.pdf)
[^undesirable-difficulty]: *Undesirable Difficulty Effects in the Learning of High-Element-Interactivity Materials* (PMC). The reversal of desirable difficulty when working memory is already saturated. [ncbi.nlm.nih.gov](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6099118/)
[^worked-example]: *Desirable difficulties, worked examples, and completion problems*, Frontiers in Psychology. The worked-example effect for novices and its reversal toward incomplete/completion examples with expertise. [frontiersin.org](https://www.frontiersin.org/journals/psychology/articles/10.3389/fpsyg.2019.01623/xml)
[^generation-effect]: *The Generation Effect*, Structural Learning. Support for generation over review as the stronger desirable difficulty. [structural-learning.com](https://www.structural-learning.com/post/generation-effect-active-learning)
[^anthropic-fellows]: *Anthropic Fellows Program*, Anthropic (Greenhouse). Source for the program's tracks, its selection on demonstrated capability, and the no-internships/12-month reapplication terms. [job-boards.greenhouse.io](https://job-boards.greenhouse.io/anthropic/jobs/5023394008)
[^unsourced-fluency]: **No source given.** Fluency as a cue for judged understanding, and the illusion of explanatory depth, are reported here from the general literature; no paper in this piece's source list establishes either. Treat both as inference until they carry a citation. The argument does not rest on them alone — the METR result is the checkable version of the same claim.
[^unsourced-rpe]: **No source given.** The reward-prediction-error account of boredom, and the learning-progress framing of curiosity-driven agents, are asserted from background literature that is not in this piece's source list. Treat this paragraph as inference. It motivates the design of the loops below; it is not evidence for them.

---

## Sources

Compensation and hiring data:

- [Anthropic Salaries — Levels.fyi](https://www.levels.fyi/companies/anthropic/salaries)
- [Anthropic Software Engineer Salary — Levels.fyi](https://www.levels.fyi/companies/anthropic/salaries/software-engineer)
- [Anthropic Is Paying Up to $1.3 Million for Some AI Roles in 2026 — Metaintro](https://www.metaintro.com/blog/anthropic-1-3-million-ai-roles-salary-2026)
- [Anthropic Salary (2026): Engineer & Researcher Compensation Bands — CTAIO](https://ctaio.dev/en/salary/anthropic-salary/)
- [OpenAI Salaries — Levels.fyi](https://www.levels.fyi/companies/openai/salaries)
- [OpenAI Salary 2026: $249K–$1.28M TC, PPU Equity — JobsByCulture](https://jobsbyculture.com/blog/openai-compensation-2026)
- [OpenAI Salary (2026): L4–L7 Compensation, PPUs & Signing Bonuses — CTAIO](https://ctaio.dev/en/salary/openai-salary/)
- [How Much OpenAI Employees Make — Entrepreneur](https://www.entrepreneur.com/business-news/how-much-openai-employees-make-salaries-685000)

Primary hiring-criteria sources:

- [Careers — Anthropic](https://www.anthropic.com/careers)
- [Research Engineer / Scientist, Alignment — Anthropic (Greenhouse)](https://job-boards.greenhouse.io/anthropic/jobs/4631822008)
- [Research Engineer / Scientist, Alignment, London — Anthropic (Greenhouse)](https://job-boards.greenhouse.io/anthropic/jobs/4610158008)
- [Anthropic Fellows Program — Anthropic (Greenhouse)](https://job-boards.greenhouse.io/anthropic/jobs/5023394008)
- [Jobs — Anthropic](https://www.anthropic.com/careers/jobs)
- [Research Engineer — OpenAI](https://openai.com/careers/research-engineer)
- [Anthropic Research Engineer Interview 2026 — Sundeep Teki](https://www.sundeepteki.org/advice/anthropic-research-engineer-interview-2026)
- [When AI builds itself — Anthropic](https://www.anthropic.com/institute/recursive-self-improvement)
- [Taste Is the Next Capability AI Will Crack — Wenbo Pan](https://www.wenbo.io/blog/taste-scaling/)

Perception–reality gap and cognitive offloading:

- [METR: Measuring the Impact of Early-2025 AI on Experienced Open-Source Developer Productivity](https://metr.org/blog/2026-02-24-uplift-update/)
- [AI Coding Tools Made Developers 19% Slower: METR Study](https://letsdatascience.com/blog/developers-thought-ai-made-them-faster-the-data-said-otherwise)
- [The Vibe-Check Protocol: Quantifying Cognitive Offloading in AI Programming (arXiv)](https://arxiv.org/pdf/2601.02410)
- [Using Biometrics to Understand AI-Assisted Coding Performance and its Perception (arXiv)](https://arxiv.org/pdf/2606.20598)
- [AI-overdependence and human cognitive decline — ScienceDirect](https://www.sciencedirect.com/science/article/pii/S2451958826001764)
- [Mitigating "Epistemic Debt" in Generative AI-Scaffolded Novice Programming using Metacognitive Scripts (arXiv)](https://arxiv.org/html/2602.20206v2)
- [The Skill Atrophy Trap — TianPan.co](https://tianpan.co/blog/2026-04-19-skill-atrophy-ai-augmented-engineering)
- [A Review of the Negative Effects of Digital Technology on Cognition (arXiv)](https://arxiv.org/pdf/2603.10025)

Learning mechanism:

- [Metcalfe & Bjork — Desirable Difficulties and Studying in the Region of Proximal Learning (PDF)](https://www.columbia.edu/cu/psychology/metcalfe/PDFs/Metcalfe-BjorkVolSubmitFeb14Final.pdf)
- [Desirable difficulties, worked examples, and completion problems — Frontiers in Psychology](https://www.frontiersin.org/journals/psychology/articles/10.3389/fpsyg.2019.01623/xml)
- [Undesirable Difficulty Effects in the Learning of High-Element-Interactivity Materials — PMC](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6099118/)
- [The Generation Effect — Structural Learning](https://www.structural-learning.com/post/generation-effect-active-learning)
