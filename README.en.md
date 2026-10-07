[English](README.md) · 简体中文

# amber-kimi

> ⚠️ **Correction (2026-10-02, second)**: one defense case, A-d511f9e8, is now NA on every lane (the exam room did not grade the file the model gave in, and the grader asks for something the task text does not say). The denominator and the **number of passed cases do not change**; every lane's total now carries `'`. In this repo's issue tables, read that cell as NA. Everything else stays as published; the [correction notice](https://github.com/getaskclaw/amber/blob/main/docs/corrections-2026-10-02-a-d511f9e8.en.md) governs.

Public results from running Kimi (Moonshot AI)'s official coding endpoint (`api.kimi.com/coding`) models against the private **AMBER** benchmark. Results only — never the questions.

## What this is

- A 'lane' is one vendor's shop/API for a model name; a 'case' is one task, a 'run' is one sitting (a case with more than one variant has more runs).
- One `results/YYYY-Www.md` per period: same paper, same harness (the program that runs the exam and scores it), full library; models and effort band (the thinking-effort setting)s of this endpoint side by side.
- Each issue reports: library size and hashes, per-case defect-hunt score and pass/fail, terminal states (how the run ended), token usage and latency, environment fingerprint, and verdicts written under evidence rules.
- Questions, oracles, transcripts (full answer logs)s and intermediate artifacts are **never published** (see "Publication rules" below).
- Sister repos: [amber-gpt](https://github.com/getaskclaw/amber-gpt), [amber-crof](https://github.com/getaskclaw/amber-crof), [amber-ollama](https://github.com/getaskclaw/amber-ollama), [amber-devin](https://github.com/getaskclaw/amber-devin), [amber-opencode](https://github.com/getaskclaw/amber-opencode), [amber-commandcode](https://github.com/getaskclaw/amber-commandcode), [amber-deepseek](https://github.com/getaskclaw/amber-deepseek), [amber-workbuddy](https://github.com/getaskclaw/amber-workbuddy), [amber-doubao](https://github.com/getaskclaw/amber-doubao), [amber-goldenpotato](https://github.com/getaskclaw/amber-goldenpotato), [amber-stepfun](https://github.com/getaskclaw/amber-stepfun). This repo's benchmark axis is **models and effort bands of Kimi's official coding endpoint** — first entry is k3 @ high, full library; sibling models (`k3-256k`, `kimi-for-coding`, …) and other bands join later. Cross-repo citations always carry date and band.
- AMBER is an agentic, real-work benchmark (coding / ops / review / vision / requirement-drift (the requirements change mid-task)). Spec and tools: [getaskclaw/amber](https://github.com/getaskclaw/amber); the questions themselves stay private.

## W38 in one minute

![W38 scorecard: k3 17/23, straight into the #2 tie](docs/images/scorecard-2026-w38.en.png)

Kimi official coding endpoint, high band, same 23 cases same hashes: **k3 17/23** (15/21 on the public 21-case subset) — coding 5/6 (full marks on the hard discriminator A-442d4aab 7/7 and A-569dbe0d 10/10) + ops 6/6 clean sweep + the riding-line vision case A-ea80d793 passed (3.0); weaknesses: verification 0/3 and an unfinished UI deliverable. Full matrix and lane ledger in the [2026-W38 issue](results/2026-W38.md). Chart sources live next to the PNGs (`docs/images/`, Vega-Lite).

### Extra race: k3 vs K2.8 Preview (Addendum 09-17)

![k3 vs K2.8 completion by capability face](docs/images/duel-face-k3-vs-k28.en.png)
![Same band, less burn](docs/images/duel-efficiency-k3-vs-k28.en.png)

On Sep 11 Moonshot quietly re-pointed `kimi-for-coding` to **K2.8 Preview** (model ID unchanged). Same-library, same-band duel: **coding / text / requirement-drift faces match k3 paper for paper, at 27% less wall clock**; case-level 14/23, with all three gaps on known riding-line cases. But on the adversarial-review case it scored **-17 (k3: -2 — a hallucination flood)**: **K2.8 is fine for daily coding lanes, not fit for review lanes**. It beats k3 on the defensive-validation case (7/9 vs 4/9). Full table: the [2026-W38 issue](results/2026-W38.md), "Addendum 2026-09-17" at the end.

## Publication rules (red lines)

1. We publish: scores and totals, token usage, speed, verdicts.
2. We never publish: question content, oracles/graders, transcripts, candidate workspaces, or any intermediate artifact that could rebuild a question.
3. Every issue pins: model ID, effort band, date (UTC), harness version, and a per-case content hash (bundle_sha (per-case content-hash fingerprint)). Hashes are checked against the public hash index in [amber](https://github.com/getaskclaw/amber) to prove the paper has not changed.
4. Case numbering and question structure are private: public results refer to cases only by stable aliases (A-xxxxxxxx, hash-derived) plus the bundle hash; internal case IDs, variant names, and question descriptions never appear.
5. Tone: this is community measurement, not an attack on any vendor. Let the data speak; keep the wording simple.

## One methods note

Same model name, same provider, two runs can still score differently — sampling parameters, load, and server-side versions all drift. Every conclusion here carries a date and a band, and we re-run on a fixed rhythm. A single day's number is a snapshot, not a law.

## Results index

| Issue | Candidate | Score (23 cases / 21-case subset) | One-liner |
|---|---|---|---|
| [2026-W38](results/2026-W38.md) | **k3** (official coding endpoint flagship) | **17/23** (15/21) | Straight into the #2 tie; coding 5/6 + ops 6/6 + vision pass; verification 0/3, incomplete UI deliverable |
| ↳ [Addendum 09-17](results/2026-W38.md) | **K2.8 Preview** (`kimi-for-coding`) | **14/23** (12/21) | Matches k3 paper for paper on coding / text / req-drift at 27% less wall clock; adversarial review -17 (hallucination flood) — not fit there; defensive validation beats k3 (7/9 vs 4/9) |
| [2026-W38 correction notice](results/2026-W38-correction.en.md) | W38 full-library review: 0 cells reversed · 4 held here | 4 k3 papers held (high / low / spot + one more main-table cell); the 17/23 headline may move up after re-exam |

## Disclaimer

Not affiliated with or sponsored by Moonshot AI / Kimi. Scores are snapshots of a specific week and band, not buying advice.