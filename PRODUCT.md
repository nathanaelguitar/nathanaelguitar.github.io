# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

## Stack

static HTML/CSS/JS — user's answer. Single self-contained page, no build step, deployed as a GitHub Pages user site at `nathanaelguitar.github.io`. Constrains the build: no framework runtime, no npm dependency at serve time, assets inlined or committed.

## Users

Primary: technical recruiters, hiring managers, and engineering/data-science interviewers evaluating Nathanael Gill for analytics-engineering, ML-engineering, and applied-AI roles. They arrive from a resume, a LinkedIn profile, or a GitHub profile link, usually with under two minutes of attention, often on a phone between other candidates. Their job is to decide quickly whether the depth claimed on the resume is real.

Secondary: peers and collaborators (Cornell MSBA cohort, open-source contacts) who want to find a specific project's repo.

## Product Purpose

A personal project showcase that converts resume bullets into verifiable evidence. Success is a visitor leaving able to name at least two specific things he built, with a number or mechanism attached, and knowing how to reach him. It is not a blog, not a services pitch, and not a comprehensive repo index.

## Positioning

The differentiator is that the work is shipped and measured, not described: an on-device LLM app with real iOS and Android codebases, a 27B fine-tune with published holdout metrics, an evaluation framework with a saved model and confusion matrix. Most portfolios at this career stage list coursework; this one can show artifacts and numbers a neighboring candidate could not truthfully copy.

## Operating Context

Visitors scan on desktop and mobile, click through to GitHub, and often open two or three repos in tabs. Several of the strongest projects live in private repositories and cannot be linked. Some are team projects with named collaborators. Some use licensed data (WRDS/IBES) that cannot be republished. Every one of these is a factual constraint on how the work may be presented.

## Capabilities and Constraints

- Content is fixed at build time; there is no CMS, no backend, no analytics requirement.
- Must work with JavaScript disabled for core reading and navigation.
- Private repos are shown with a "Private repository" state and **no hyperlink**. Confirmed by the user.
- Contact surface is email (ng542@cornell.edu), GitHub (nathanaelguitar), LinkedIn (nathanaelgill) only. Phone number and street address are deliberately excluded from a public, indexed page. Confirmed by the user.
- No resume PDF is hosted; the resume contains the excluded personal details.
- Team projects must name the team. Forks must be identified as forks.
- `Supply_Chain` is featured **at the user's explicit request** (2026-08-13), after the concern was raised that the repository contains assignment briefs and `U2_ANSWER_KEY.txt`. The page describes the optimization work only; pruning the answer key from that repository is the user's call.

## Brand Commitments

Name: Nathanael Gill. No existing personal logo, mark, palette, or type system exists — nothing visual is inherited or binding.

## Evidence on Hand

Real, verified from the repositories (not to be embellished):

- **CanopyChat** (`local_ai_aether`, public, 124 commits) — cross-platform private local-first LLM chat. `iphone/` SwiftUI app, `android/` Kotlin/Jetpack Compose port, `backend/` Kotlin/Ktor OpenAI-compatible proxy. Quantized GGUF on-device inference, web-search RAG, subscriptions, contributor telemetry. Live legal/support site at https://nathanaelguitar.github.io/canopy_publicsite/ (repo `canopy_publicsite`, public). **The inference model itself is a proprietary fine-tune the user trained on his DGX Spark** (the same hardware used for the Qwen/IBES adapter). The app is currently in beta on TestFlight, ahead of an App Store / Play Store release — confirmed 2026-08-13. This supersedes any earlier "shipped as source, no app-store release" framing.
- **Qwen3.6-27B QLoRA on WRDS/IBES** (`ML_Class_LORA`, public, 56 commits) — 5-person Cornell team (Finn Kliewer, Tyler Fuentes, Richie Gray, Om Patel, Nathanael Gill). Trained on a dedicated NVIDIA DGX Spark. Includes a PySpark WRDS/IBES bronze-silver-gold pipeline, a pinned FinGPT submodule, and `eval/evaluate_base_vs_adapter.py`. Published aggregate metrics in `docs/shareable-evals/`: WRDS 10k holdout base accuracy 0.449 → adapter 1.000; base macro-F1 0.541 → 1.000; **base JSON parse-failure rate 0.534 → 0.000**; adapter exact-JSON-match 0.999. Public FIQA benchmark: 1k adapter 0.8125 accuracy, 10k adapter 0.7969. **Honest reading, which must be preserved: the headline holdout gain is dominated by schema/instruction-following — the base model failed to emit parseable JSON on over half of prompts. FIQA is the fairer generalization number.** Raw WRDS data, predictions, adapters, and checkpoints are licensed/local and are not in the repo.
- **VC Scout** (`team17-vc-scout-model`, public fork, 37 commits) — Cornell capstone Project #32, Team 17: Mia Murphy, Finn Kliewer, Kayvon Jafarzadeh (GitHub `K4yv0n`), Om Patel, Nathanael Gill — confirmed from the repo README and GitHub contributors list. **The repository is forked FROM Kayvon Jafarzadeh's original** (`K4yv0n/team17-vc-scout-model`), not the reverse — do not imply the user originated the repo. Predicts ln(Valuation $B) for 1,060 modeled unicorn companies (1,074 raw). Gradient Boosting best: CV R² 0.46, Test R² 0.51, MAE 0.44 (ln), against a mean baseline of CV R² -0.01. Explicitly framed conditional-on-unicorn to avoid survivorship bias; funding efficiency deliberately excluded as a leaky feature. Ships a 10-slide deck, `model_stats.json` as source of truth, and a genuinely interactive self-contained dashboard live at `dashboards/VC-Scout-Dashboard.html`, plus a presentation deck at `presentation/vc-scout-deck.html` (theme toggle, Tabler icons) — served via GitHub Pages at https://nathanaelguitar.github.io/team17-vc-scout-model/dashboards/VC-Scout-Dashboard.html, linked from the page.
- **Discovery-call agent evaluation** (`AgenticSales`, public, 51 commits) — offline scenario-based evaluation framework for AI discovery-call agent policies. 8–12 canonical scenarios; compares a baseline scripted agent, a freeform LLM agent, and a guided LLM agent on rubric score, discovery coverage, objection resolution, and derailment rate. PySpark call-level feature pipeline. Saved logistic-regression baseline (`baseline_logistic.pkl`, `baseline_eval.json`): **120 synthetic calls, 96 train / 24 test, accuracy 0.958, precision 1.00, recall 0.80, F1 0.889** — the small test set must be stated wherever the accuracy is.
- **OpenClaw recursive agent memory** (private repo) — extended the OpenClaw open-source agent codebase with recursive agent memory: SQLite structured storage plus embedding-based semantic search, enabling retrieval of prior logs and time-aware context for persistent agent state. Cannot be linked. The upstream repository's commit count is inherited and must never be presented as his.
- **Naming** — the iOS target builds as `AetherChat`; the shipping product identity (and its legal/support site) is `CanopyChat`. The user refers to the project as AetherChat, which is what the page leads with.
- **Agentic sales-automation pipeline** (private repo) — orchestrates web scraping, lead enrichment, automated email outreach, and call qualification for sourcing potential acquisition targets; migrated from local Docker to a Linux VM on Oracle Cloud Infrastructure for persistent cloud execution. Client-identifying material is under NDA; no client may be named and the repo may not be linked.
- **Forecast accuracy pipeline** (`digital_operations`, public, 12 commits) — Walmart sales forecast ETL computing MAD, MAPE, sales-to-forecast ratio, and bias, exporting a multi-sheet Excel report built on live SUMPRODUCT formulas rather than static values.
- **NLP / LDA topic modeling** (`NLPs`, public, 16 commits) — 24-topic LDA over the middle-1000 companies by market cap, cross-tabulated against GICS industry groups. Measured coherence: Utilities 96.2%, Insurance 95.0%, Banks 91.8%, Semiconductors 81.2%, Autos 71.4%.
- **Professional background** — HCA Healthcare Analytics Engineer Intern (Databricks/PySpark Medallion ETL, Power BI, Azure Key Vault monitoring); Metlang Analytic Linguist with security clearance; LJW Associates project manager. Cornell MSBA, completed 2026, MTSU BA Foreign Languages magna cum laude.
- **Leadership** — President, Cornell Data Science Club (Aug 2025–present).

Absences that must not be fabricated: no stars, no downloads, no users, no App Store release, no press, no testimonials, no employer endorsements, no revenue. `localai_app` is a Kotlin Multiplatform **scaffold** whose chat responses are explicitly fake — it may not be presented as a second shipping app.

Added after the first review round (all verified in the repositories):

- **Retail operations** (`digital_retail_operations`, public) — five notebooks: ingestion and quality checks, demand patterns/EDA, basket analysis and cross-sell, forecasting and staffing model, operational recommendations. Real committed outputs: `association_rules.csv`, `staffing_plan.csv`, `hourly_profile.csv`, `weekday_hour_profile.csv`, `top_products.csv`, `executive_summary.csv`, plus demand-pattern and staffing-heatmap figures. Low commit count (3) but substantial content — commit count is not a proxy for depth here.
- **Supply chain optimization** (`Supply_Chain`, public, 20 commits) — graduate coursework: inventory optimization to maximise supply-chain efficiency, and production capacity allocation under constraint. Python plus Excel deliverables. **The repository also contains assignment briefs and `U2_ANSWER_KEY.txt`; the user was told to prune these.** Featured at the user's explicit request after the exclusion was raised.
- **Revenue forecasting** (`Predictive_Analytics`, private, 7 commits) — real QuickBooks exports; revenue defined strictly as invoice issuance, normalized monthly, deliberately conservative one-year projection with complex models avoided to prevent inflated valuation inputs. Private; no client named.
- **Demand management** (`Demand_Management`, **public as of 2026-08-13**, 11 commits) — pricing-optimization coursework with an ingestion layer (Excel read/validate) and processing layer (case-level to unit-level, margin/market-share/profit metrics).
- **AlphaAgent_Deck** (public, 4 commits) — Python that generates a pitch deck, use-of-funds model, and monthly projection workbook from code.
- **VisionClaw is NOT the user's work** and must never appear. Removed 2026-08-13 on the user's correction.

Model-comparison rows for VC Scout (OLS, Ridge alpha=30, Lasso alpha=0.005, KNN k=25, random forest, gradient boosting) and the 80/20 seed-17 split are published in that repository's README and `model_stats.json`.

## Product Principles

1. **Every claim traces to an artifact.** A number on the page exists in a repo file, or it does not go on the page.
2. **State the caveat next to the number.** Small test sets, team authorship, fork status, and schema-driven gains are disclosed inline, not buried. Honest framing is the credibility mechanism, not a tax on it.
3. **A dead link costs more than a missing link.** Private work is shown as private; nothing hyperlinked may 404.
4. **Depth over inventory.** A few projects understood beats thirty-seven repos listed.
5. **Two minutes, one thumb.** The scanning path works on a phone with no interaction required.

## Accessibility & Inclusion

No user-specific requirement was established. Standard obligations apply: WCAG AA contrast, keyboard-operable navigation, visible focus, semantic landmarks and heading order, respect for `prefers-reduced-motion`, and full content legibility without JavaScript.

## Corrections logged 2026-08-13

- Nathanael **completed** the Cornell MS in Business Analytics in 2026. He is no longer a candidate; page copy updated in the title block and the closing cue.
- The GitHub handle `nathanaelguitar` dates from opening the account to learn Python on DataCamp. An earlier draft invented "older than the career and I have stopped trying to explain it" — that was fabricated and is removed. **Do not invent biographical colour.**
- `VisionClaw` is not his work. Never include it.
- The private "iOS agent client" row was removed at his request.
- `Demand_Management` made public after untracking `bana6390_u3_answer.md`, `q4_answer.md`, `q5_answer.md`, `__pycache__`.
- `Predictive_Analytics` **must not be made public as-is**: `data/2021_sales.xls` through `2025_sales.xls` and `data/sales.desc` are committed real QuickBooks exports containing a customer-name column, directly contradicting that repo's own `.gitignore` ("Data files (confidential)"), its `data/README.md` ("excluded from version control for confidentiality"), and its `scripts/check_no_data_committed.py` guard. Flipping a private repo to public exposes full history, so untracking at HEAD is not sufficient.

## Corrections logged 2026-08-13 (second round)

- Canopy's on-device model is not just a quantized open-weight model — it is a **proprietary fine-tune** the user trained himself on his DGX Spark. State this plainly in cue 10; do not undersell it as "just" GGUF quantization of a third-party model.
- The app is in **beta on TestFlight now**, with an App Store / Play Store release expected soon. This is newer and stronger than the previous "no app-store release" note — update forward, do not revert to the older framing if this file is stale in a future session.

## Corrections logged 2026-08-13 (third round)

- Venue changed from Nashville/Ithaca (past job/school cities) to New York, NY and San Francisco, CA (target markets) — job-history location mentions elsewhere on the page (HCA in Nashville, Cornell in Ithaca) are unchanged since those are factual employment/education locations, not "venue."
- VC Scout capstone team fully named: Mia Murphy, Finn Kliewer, Kayvon Jafarzadeh, Om Patel, Nathanael Gill. Do not add unverifiable honorifics about any teammate (e.g. "prominent AI creator") — state only what the repo confirms (name, GitHub handle, that the repo is forked from his original).
- Live interactive VC Scout dashboard linked: `dashboards/VC-Scout-Dashboard.html`, confirmed serving at 200 via GitHub Pages.
