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
- Coursework repos containing graded submissions or answer keys (`Supply_Chain`) are excluded for academic-integrity reasons.

## Brand Commitments

Name: Nathanael Gill. No existing personal logo, mark, palette, or type system exists — nothing visual is inherited or binding.

## Evidence on Hand

Real, verified from the repositories (not to be embellished):

- **CanopyChat** (`local_ai_aether`, public, 124 commits) — cross-platform private local-first LLM chat. `iphone/` SwiftUI app, `android/` Kotlin/Jetpack Compose port, `backend/` Kotlin/Ktor OpenAI-compatible proxy. Quantized GGUF on-device inference, web-search RAG, subscriptions, contributor telemetry. Live legal/support site at https://nathanaelguitar.github.io/canopy_publicsite/ (repo `canopy_publicsite`, public).
- **Qwen3.6-27B QLoRA on WRDS/IBES** (`ML_Class_LORA`, public, 56 commits) — 5-person Cornell team (Finn Kliewer, Tyler Fuentes, Richie Gray, Om Patel, Nathanael Gill). Trained on a dedicated NVIDIA DGX Spark. Includes a PySpark WRDS/IBES bronze-silver-gold pipeline, a pinned FinGPT submodule, and `eval/evaluate_base_vs_adapter.py`. Published aggregate metrics in `docs/shareable-evals/`: WRDS 10k holdout base accuracy 0.449 → adapter 1.000; base macro-F1 0.541 → 1.000; **base JSON parse-failure rate 0.534 → 0.000**; adapter exact-JSON-match 0.999. Public FIQA benchmark: 1k adapter 0.8125 accuracy, 10k adapter 0.7969. **Honest reading, which must be preserved: the headline holdout gain is dominated by schema/instruction-following — the base model failed to emit parseable JSON on over half of prompts. FIQA is the fairer generalization number.** Raw WRDS data, predictions, adapters, and checkpoints are licensed/local and are not in the repo.
- **VC Scout** (`team17-vc-scout-model`, public fork, 37 commits) — Cornell capstone Project #32, Team 17. Predicts ln(Valuation $B) for 1,060 modeled unicorn companies (1,074 raw). Gradient Boosting best: CV R² 0.46, Test R² 0.51, MAE 0.44 (ln), against a mean baseline of CV R² -0.01. Explicitly framed conditional-on-unicorn to avoid survivorship bias; funding efficiency deliberately excluded as a leaky feature. Ships a 10-slide deck, `model_stats.json` as source of truth, and self-contained HTML dashboards.
- **Discovery-call agent evaluation** (`AgenticSales`, public, 51 commits) — offline scenario-based evaluation framework for AI discovery-call agent policies. 8–12 canonical scenarios; compares a baseline scripted agent, a freeform LLM agent, and a guided LLM agent on rubric score, discovery coverage, objection resolution, and derailment rate. PySpark call-level feature pipeline. Saved logistic-regression baseline (`baseline_logistic.pkl`, `baseline_eval.json`): **120 synthetic calls, 96 train / 24 test, accuracy 0.958, precision 1.00, recall 0.80, F1 0.889** — the small test set must be stated wherever the accuracy is.
- **OpenClaw recursive agent memory** (private repo) — extended the OpenClaw open-source agent codebase with recursive agent memory: SQLite structured storage plus embedding-based semantic search, enabling retrieval of prior logs and time-aware context for persistent agent state. Cannot be linked. The upstream repository's commit count is inherited and must never be presented as his.
- **Agentic sales-automation pipeline** (private repo) — orchestrates web scraping, lead enrichment, automated email outreach, and call qualification for sourcing potential acquisition targets; migrated from local Docker to a Linux VM on Oracle Cloud Infrastructure for persistent cloud execution. Client-identifying material is under NDA; no client may be named and the repo may not be linked.
- **Smart-glasses agent work** (private) — Meta Ray-Ban + Gemini Live + OpenClaw integration (`VisionClaw`, 146 commits). Exploratory; no shipped claim attached.
- **Forecast accuracy pipeline** (`digital_operations`, public, 12 commits) — Walmart sales forecast ETL computing MAD, MAPE, sales-to-forecast ratio, and bias, exporting a multi-sheet Excel report built on live SUMPRODUCT formulas rather than static values.
- **NLP / LDA topic modeling** (`NLPs`, public, 16 commits) — 24-topic LDA over the middle-1000 companies by market cap, cross-tabulated against GICS industry groups. Measured coherence: Utilities 96.2%, Insurance 95.0%, Banks 91.8%, Semiconductors 81.2%, Autos 71.4%.
- **Professional background** — HCA Healthcare Analytics Engineer Intern (Databricks/PySpark Medallion ETL, Power BI, Azure Key Vault monitoring); Metlang Analytic Linguist with security clearance; LJW Associates project manager. Cornell MSBA candidate (May 2026), MTSU BA Foreign Languages magna cum laude.
- **Leadership** — President, Cornell Data Science Club (Aug 2025–present).

Absences that must not be fabricated: no stars, no downloads, no users, no App Store release, no press, no testimonials, no employer endorsements, no revenue. `localai_app` is a Kotlin Multiplatform **scaffold** whose chat responses are explicitly fake — it may not be presented as a second shipping app.

## Product Principles

1. **Every claim traces to an artifact.** A number on the page exists in a repo file, or it does not go on the page.
2. **State the caveat next to the number.** Small test sets, team authorship, fork status, and schema-driven gains are disclosed inline, not buried. Honest framing is the credibility mechanism, not a tax on it.
3. **A dead link costs more than a missing link.** Private work is shown as private; nothing hyperlinked may 404.
4. **Depth over inventory.** A few projects understood beats thirty-seven repos listed.
5. **Two minutes, one thumb.** The scanning path works on a phone with no interaction required.

## Accessibility & Inclusion

No user-specific requirement was established. Standard obligations apply: WCAG AA contrast, keyboard-operable navigation, visible focus, semantic landmarks and heading order, respect for `prefers-reduced-motion`, and full content legibility without JavaScript.
