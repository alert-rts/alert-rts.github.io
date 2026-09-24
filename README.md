# ALERT: Agents for Language-Guided Execution of Revocable Tasks in Real-Time Strategy Games

**Anonymous submission — under double-blind review at ICLR.**

📄 Project page: **[alert-rts.github.io](https://alert-rts.github.io)** — a visual companion to the submission, with the system diagram, a directive's full lifecycle, the six execution gates, release accounting, and a demo video.

---

## What is ALERT?

Real-time strategy (RTS) demands rapid responses to a changing battlefield *and* plans that persist across those responses. Under human direction, both must remain **answerable to orders that can change during play**. Existing RTS agents are judged by whether they win; ALERT asks a different question:

> Did the agent do what it was told, keep doing it while the world moved, and stop when the order was withdrawn?

ALERT benchmarks the interaction between **System 1 execution**, **System 2 understanding and planning**, and **continuing human authority** in full *Command & Conquer: Red Alert 2* matches — scoring requested effects separately from victory.

## Highlights

- **⏱️ The engine waits for nobody.** Clock-paced evaluation advances the game 15 logic steps per second *during* model inference. A plan can go stale before it arrives; the executor must act while awaiting further deliberation. No pausing, no tick-gated turn-taking.
- **🔄 Live, revocable instructions.** A commander can order a retreat, then revise or revoke it before the force reaches safety. Evaluator-side contracts specify scope, duration, constraints, and revocation; matched controls separate requested effects from autonomous play.
- **🧭 Authority lives outside the transcript.** A typed order ledger stores verbatim orders, commitments, ownership, and revocation state outside model memory. System 1 freedom to act on new observations never authorizes replacing the commander's objective.
- **🔍 Diagnosis, not a single score.** Six ordered execution gates — Goal, Plan, Tracking, Grounding, Execution, Verification — join behavioral-intent readings, commitment and controller traces, independent world-state predicates, and post-hoc position value. Each gate names the component a confirmed failure would repair.
- **🛠️ Findings feed tested repairs.** *Self-evolve* applies diagnosis to harness revision under frozen re-measurement — model weights stay fixed; claims stay bounded.

## Headline findings

| Finding | Evidence |
|---|---|
| All released retreat directives produced accepted movement orders | 7 / 7 in the 24-match clock-paced study |
| …yet a tracking defect retired commitments before controller-confirmed arrival | 6 / 7, discharged 0–2 ticks after a new order identifier appeared |
| Targeted revocation works where tested | 10 / 10 applicable countermand runs retire exactly the guard order |
| Directive script dominates measured outcome across models | 144 tick-paced runs; six models, 12 scripts, two orientations |
| Model identity remains distinguishable at intake | 0.903 vs 0.665 average, 14 strict wins / 0 losses in 24 matched groups (p = 0.0001) |

The benchmark reports evidence boundaries as boundaries: of 79 released directive occurrences, 23 carry an implemented external predicate; unadjudicated intent labels and incomplete gate evidence are stated, not averaged away.

## What's in this repository

This repository serves the project page (GitHub Pages, plain HTML — no trackers, no external requests):

```
index.html      the project page
style.css       styling
assets/         paper figures, demo video, poster frame
```

**Note for reviewers:** the demo clip currently on the page is an illustrative concept render of a match's directive lifecycle; real gameplay capture will replace it. Code, the directive corpus (23 scripts / 70 cards; paper corpus 12 scripts / 49 cards), and recorded trajectories will be released upon publication.

## Citation

```bibtex
@inproceedings{
  anonymous2027alert,
  title   = {{ALERT}: Agents for Language-Guided Execution of Revocable Tasks in Real-Time Strategy Games},
  author  = {Anonymous},
  booktitle = {Submitted to the International Conference on Learning Representations},
  year    = {2027},
  note    = {Under double-blind review}
}
```
