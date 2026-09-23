# Deepan Singh, MD, FAPA

Physician-founder and CEO of [DNAi Systems](https://dnai.systems). I build [Asha](https://askasha.org), a retrieval-grounded fiduciary medical AI, and the platform it runs on.

## What I build

Asha is a neurosymbolic medical agent. The language model is the verbalization layer; the intelligence sits around it: KIL retrieval over a curated Qdrant corpus (144M+ vectors, ~1,071 collections, ~314 of them knowledge-source), an Epistemic Arena where candidate claims compete before anything is said, and META_CORRECT, a deterministic post-emission corrector. US Patent 12,555,008 B1, granted 2026-02-17.

Every benchmark number DNAi publishes lives with its pipeline, grader, and artifacts at [dnai.systems/benchmarks](https://dnai.systems/benchmarks). Three rows from the current register:

- HealthBench Hard, 1,000 items, official gpt-4.1 grader: Asha 42.0 against 29.4 for its own bare composer (GPT-6 Astra), +12.6 pp paired on the same items (run 2026-09-21).
- MedQA USMLE, 1,273 locked items, single shot: 95.52%, 0 parse failures (2026-05-04).
- psychosis-bench, 96 intervention-eligible turns: 95.8% safe-intervention rate against 30.2% for the same backbone without the architecture (2026-05-11).

## Public repositories, in reading order

1. [asha-bench-public](https://github.com/EndlessRay/asha-bench-public): bit-exact reproducible artifacts for MedQA, META_CORRECT, psychosis-bench, and enclomiphene-bench. SHA-256 locked inputs, pre-registered hypotheses, retractions kept in the same history.
2. [asha-healthbench-2026-06-26](https://github.com/EndlessRay/asha-healthbench-2026-06-26): consolidated HealthBench runs (standard, Hard, Professional), pipeline glossary, 24-page preprint.
3. [asha-aom-chart-2026-08](https://github.com/EndlessRay/asha-aom-chart-2026-08): verbatim production traces on a clinician-authored locked pediatric protocol.
4. [asha-a2a](https://github.com/EndlessRay/asha-a2a): Asha over the A2A protocol, with the provenance contract every response carries. Live at `api.askasha.org`.

## Where the code is

The Citadel monorepo (FastAPI, React + Vite, Qdrant, PostgreSQL, Redis, Docker; about 3,200 tracked files and 3,000 commits on main since December 2025, 97% of them by the two physician co-founders) is private because it runs a live medical product with real users. Walkthrough on request.

Co-founder: [Paridhi Anand, MD](https://github.com/circumferance).

Contact: dsingh@dnai.systems
