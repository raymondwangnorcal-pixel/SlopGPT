# Project Decisions

## DEC-0001 — Use a repository-scoped REA integration

- Date: 2026-10-20
- Owner: user
- Status at record: active
- Decision: Install the REA reverse-engineering skill and its version-pinned MCP server configuration at repository scope.
- Rationale: REA should be available for SlopGPT investigations without enabling it for unrelated repositories, while pinning the server package keeps the shared tool behavior reproducible.
- Scope: The repository-local `.agents/skills/reverse-engineer-anything` skill and `.codex/config.toml` MCP registration.
- Implementation: pending
- Recorded against HEAD: not applicable
- Supersedes: none
- Evidence: Repository-local REA skill and MCP configuration requested in this conversation.
- Privacy waivers: none

## DEC-0002 — Extend the repository-scoped REA integration to Claude Code

- Date: 2026-10-20
- Owner: user
- Status at record: active
- Decision: Make the repository-scoped REA workflow available to Claude Code through a shared skill link and a private local-scope MCP registration pinned to REA 6.7.0.
- Rationale: Codex and Claude should use the same checked-in REA instructions without duplicating them, while Claude's personal registration should remain limited to this project and use its documented compact-schema compatibility settings.
- Scope: The repository-local `.claude/skills/reverse-engineer-anything` link and the SlopGPT project entry in the default Claude Code profile.
- Implementation: pending
- Recorded against HEAD: not applicable
- Supersedes: none
- Evidence: Claude Code REA compatibility requested and verified in this conversation.
- Privacy waivers: none

## DEC-0003 — Make the consumer checker the first product

- Date: 2026-10-20
- Owner: user
- Status at record: active
- Decision: Build the public consumer image-checking experience before developing the business-to-business verification API as the primary product.
- Rationale: The consumer checker is the selected entry point for validating demand, refining how evidence is communicated, and establishing the initial product experience.
- Scope: Initial product positioning, roadmap priority, user experience, and launch criteria for SlopGPT.
- Implementation: pending
- Recorded against HEAD: not applicable
- Supersedes: none
- Evidence: Product direction selected during the current design interview.
- Privacy waivers: none

## DEC-0004 — Separate verified AI origin from probabilistic verdicts

- Date: 2026-10-20
- Owner: shared
- Status at record: active
- Decision: Display "AI-generated" when a trusted watermark or valid provenance assertion explicitly identifies AI generation; otherwise display a likely or unlikely verdict with a confidence score.
- Rationale: Definitive origin signals can support a direct label, while forensic detection without such proof must communicate uncertainty.
- Scope: Consumer result taxonomy, evidence normalization, confidence presentation, and verification API semantics developed from the consumer experience.
- Implementation: pending
- Recorded against HEAD: not applicable
- Supersedes: none
- Evidence: Result behavior selected during the current design interview, with provenance semantics grounded in the repository research document.
- Privacy waivers: none

## DEC-0005 — Define the score as estimated AI-generation probability

- Date: 2026-10-20
- Owner: user
- Status at record: active
- Decision: Present the confidence score as the product's estimated probability that the uploaded image is AI-generated, such that 82 percent means the product is 82 percent confident the image is AI-generated.
- Rationale: A single directional probability gives consumers a consistent interpretation across likely and unlikely verdicts.
- Scope: Score calibration, result-page copy, detector aggregation, analytics, and future public API response fields.
- Implementation: pending
- Recorded against HEAD: not applicable
- Supersedes: none
- Evidence: Confidence-score meaning selected during the current design interview.
- Privacy waivers: none

## DEC-0006 — Include an inconclusive result state

- Date: 2026-10-20
- Owner: user
- Status at record: active
- Decision: Use an inconclusive state for non-definitive analyses whose estimated AI-generation probability is not strong enough to support either a likely or unlikely verdict.
- Rationale: Near-boundary scores and conflicting evidence should not be presented as meaningful binary conclusions.
- Scope: Consumer result taxonomy, threshold calibration, result-page copy, and future public API response fields.
- Implementation: pending
- Recorded against HEAD: not applicable
- Supersedes: none
- Evidence: Result-state policy selected during the current design interview.
- Privacy waivers: none

## DEC-0007 — Delete uploaded images after analysis by default

- Date: 2026-10-20
- Owner: user
- Status at record: active
- Decision: Process uploaded images transiently and delete the raw image after analysis, retaining it for evaluation only when the user explicitly opts in.
- Rationale: Consumer uploads may contain sensitive personal content, so raw-image retention should not be required for ordinary use of the checker.
- Scope: Upload processing, storage architecture, provider disclosures, privacy policy, logging, backups, and evaluation-data consent.
- Implementation: pending
- Recorded against HEAD: not applicable
- Supersedes: none
- Evidence: Default upload-retention policy selected during the current design interview.
- Privacy waivers: none

## DEC-0008 — Stop analysis after definitive AI provenance

- Date: 2026-10-20
- Owner: user
- Status at record: active
- Decision: Short-circuit the analysis pipeline and return an AI-generated result when a trusted watermark or valid provenance assertion definitively identifies AI generation.
- Rationale: Additional probabilistic analysis would add latency, cost, third-party exposure, and potentially confusing outputs without changing a conclusive result.
- Scope: Analysis orchestration, provider invocation, latency, cost controls, privacy exposure, and result presentation.
- Implementation: pending
- Recorded against HEAD: not applicable
- Supersedes: none
- Evidence: Pipeline behavior selected during the current design interview.
- Privacy waivers: none

## DEC-0009 — Allow paid detection services in production

- Date: 2026-10-20
- Owner: user
- Status at record: active
- Decision: Keep the initial prototype within free service tiers where practical, but permit paid third-party detection services and rate limits for production operation.
- Rationale: Free tiers can validate the concept but generally do not provide sustainable production capacity, reliability, or commercial-use terms.
- Scope: Provider selection, operating budget, rate limiting, pricing strategy, and production architecture.
- Implementation: pending
- Recorded against HEAD: not applicable
- Supersedes: none
- Evidence: Cost constraint selected during the current design interview.
- Privacy waivers: none

## DEC-0010 — Treat unresolved detector disagreement as inconclusive

- Date: 2026-10-20
- Owner: user
- Status at record: active
- Decision: Default conflicting probabilistic detector results to inconclusive unless a validated aggregation model can confidently resolve the disagreement.
- Rationale: Raw provider scores are not directly comparable, and simple averaging can conceal material conflicts while implying false precision.
- Scope: Detector aggregation, confidence calibration, fallback rules, evidence display, and future public API semantics.
- Implementation: pending
- Recorded against HEAD: not applicable
- Supersedes: none
- Evidence: Detector-conflict behavior selected during the current design interview.
- Privacy waivers: none

## DEC-0011 — Require trusted provenance for a definitive AI verdict

- Date: 2026-10-20
- Owner: shared
- Status at record: active
- Decision: Treat a valid and trusted C2PA assertion that explicitly identifies AI creation as definitive, while presenting valid but untrusted AI assertions and editable metadata only as supporting evidence.
- Rationale: C2PA distinguishes valid manifests from trusted manifests, and accepting self-signed or editable claims as definitive would allow attackers to falsely label authentic images.
- Scope: C2PA validation, signer trust registry, evidence weighting, definitive verdict rules, and result explanations.
- Implementation: pending
- Recorded against HEAD: not applicable
- Supersedes: none
- Evidence: Provenance trust policy selected during the current design interview and grounded in the official C2PA trust model.
- Privacy waivers: none

## DEC-0012 — Allow rate-limited anonymous checks

- Date: 2026-10-20
- Owner: user
- Status at record: active
- Decision: Allow consumers to analyze images without creating an account, subject to strict usage limits and proportionate abuse controls.
- Rationale: Anonymous access keeps the public checker frictionless while rate limits protect paid provider capacity from automated abuse.
- Scope: Authentication, onboarding, rate limiting, abuse prevention, privacy disclosures, and operating cost controls.
- Implementation: pending
- Recorded against HEAD: not applicable
- Supersedes: none
- Evidence: Consumer-access policy selected during the current design interview.
- Privacy waivers: none

## DEC-0013 — Expose provider-level evidence and disagreements

- Date: 2026-10-20
- Owner: user
- Status at record: active
- Decision: Show consumers an expandable evidence breakdown containing provenance, metadata, each detector's result, provider failures, and material disagreements beneath the primary verdict.
- Rationale: A simple top-level result remains approachable while detailed evidence makes the analysis auditable and prevents the combined score from concealing uncertainty.
- Scope: Result-page information architecture, provider adapters, normalized evidence records, observability, and future public API responses.
- Implementation: pending
- Recorded against HEAD: not applicable
- Supersedes: none
- Evidence: Result-transparency policy selected during the current design interview.
- Privacy waivers: none

## DEC-0014 — Use four complementary checks in the initial pipeline

- Date: 2026-10-20
- Owner: shared
- Status at record: active
- Decision: Build the initial detector pipeline from local C2PA validation, the OpenAI Content Provenance API for supported provenance signals, Sightengine for pixel-based classification, and Hive as a second probabilistic classifier.
- Rationale: The stack combines open provenance validation, provider-specific watermark evidence, and two forensic opinions while limiting initial cost and integration complexity.
- Scope: Provider adapters, orchestration, secrets, normalized evidence schema, latency, cost controls, and initial evaluation.
- Implementation: pending
- Recorded against HEAD: not applicable
- Supersedes: none
- Evidence: Initial provider stack selected during the current design interview using current official provider documentation.
- Privacy waivers: none

## DEC-0015 — Support common formats with explicit partial coverage

- Date: 2026-10-20
- Owner: shared
- Status at record: active
- Decision: Accept common photo formats using best-effort analysis, inspect original bytes for local provenance, create normalized derivatives only for compatible pixel classifiers, and report unsupported checks as not performed rather than not detected.
- Rationale: Broad input support should not imply that every provider can reliably analyze every format or that conversion preserves provenance signals.
- Scope: Upload validation, image decoding, normalization, provider routing, evidence statuses, and result-page disclosures.
- Implementation: pending
- Recorded against HEAD: not applicable
- Supersedes: none
- Evidence: File-format behavior selected during the current design interview.
- Privacy waivers: none

## DEC-0016 — Prioritize avoiding false AI accusations

- Date: 2026-10-20
- Owner: user
- Status at record: active
- Decision: Optimize probabilistic verdict thresholds primarily to minimize false positives that label authentic images as likely AI-generated, accepting a larger inconclusive region when necessary.
- Rationale: Falsely discrediting authentic media or accusing a person of deception is more harmful than withholding a probabilistic verdict when evidence is weak.
- Scope: Benchmark objectives, calibration, likely and inconclusive thresholds, safety messaging, and future API decision policies.
- Implementation: pending
- Recorded against HEAD: not applicable
- Supersedes: none
- Evidence: Error-cost priority selected during the current design interview.
- Privacy waivers: none

## DEC-0017 — Gate an unqualified probability score on benchmark validation

- Date: 2026-10-20
- Owner: user
- Status at record: active
- Decision: Keep the combined AI-generation probability labeled experimental until the full pipeline passes a held-out, transformation-aware benchmark and satisfies the defined false-positive target.
- Rationale: A numerical probability implies calibration and should not be presented without qualification until measured performance supports that interpretation.
- Scope: Evaluation datasets, release criteria, score labeling, threshold selection, regression testing, and public limitations.
- Implementation: pending
- Recorded against HEAD: not applicable
- Supersedes: none
- Evidence: Public-launch quality gate selected during the current design interview.
- Privacy waivers: none

## DEC-0018 — Keep detailed benchmark results internal

- Date: 2026-10-20
- Owner: user
- Status at record: active
- Decision: Do not publish the detailed benchmark dataset composition, performance breakdowns, or calibration results as part of the product's public trust model.
- Rationale: Public benchmark reporting is not required for the selected consumer product experience.
- Scope: Evaluation reporting, public documentation, result-page disclosures, and release communications.
- Implementation: pending
- Recorded against HEAD: not applicable
- Supersedes: none
- Evidence: Benchmark-disclosure policy selected during the current design interview.
- Privacy waivers: none

## DEC-0019 — Retain short-lived derived fingerprints for abuse prevention

- Date: 2026-10-20
- Owner: user
- Status at record: active
- Decision: Retain a salted perceptual image fingerprint and minimal result data for no more than 24 hours to cache duplicate checks and throttle near-duplicate probing, while deleting the raw image after analysis.
- Rationale: Limited derived-data retention reduces provider costs and inhibits repeated detector-evasion attempts without keeping the uploaded photo.
- Scope: Privacy disclosures, deduplication, caching, abuse detection, data expiration, and operational storage.
- Implementation: pending
- Recorded against HEAD: not applicable
- Supersedes: none
- Evidence: Derived-data retention policy selected during the current design interview.
- Privacy waivers: none

## DEC-0020 — Use AI-generated as an umbrella for material generative involvement

- Date: 2026-10-20
- Owner: shared
- Status at record: active
- Decision: Use AI-generated as the top-level verdict for fully synthesized or materially generative-edited images, while reporting whether the subtype is fully synthesized, AI-edited, or unknown and excluding routine AI-assisted enhancements.
- Rationale: A simple umbrella verdict serves consumers while subtype evidence prevents materially edited authentic photos from being misrepresented as wholly synthetic.
- Scope: Verdict semantics, confidence-score interpretation, evidence normalization, result copy, benchmark labeling, and future public API fields.
- Implementation: pending
- Recorded against HEAD: not applicable
- Supersedes: none
- Evidence: AI-generated and AI-edited terminology selected during the current design interview.
- Privacy waivers: none

## DEC-0021 — Build one API-shaped analysis service for the website and future integrations

- Date: 2026-10-20
- Owner: user
- Status at record: active
- Decision: Implement the consumer website as the first client of a private, versioned analysis service whose normalized contract can later support the public developer API.
- Rationale: Sharing the detection engine and response schema avoids rebuilding core orchestration when third-party integrations are introduced, without requiring public authentication, billing, or service guarantees in v1.
- Scope: Service boundaries, endpoint versioning, provider adapters, web integration, schemas, and future developer-platform work.
- Implementation: pending
- Recorded against HEAD: not applicable
- Supersedes: none
- Evidence: API architecture selected during the current design interview.
- Privacy waivers: none

## DEC-0022 — Model each analysis as an asynchronous job

- Date: 2026-10-20
- Owner: user
- Status at record: active
- Decision: Create an analysis job and identifier for each upload, expose progress and completion state to the consumer UI, and design the lifecycle for later polling and webhook delivery.
- Rationale: Multiple external checks can be slow or fail independently, so a job model supports timeouts, partial progress, retries, and future API delivery without relying on one long-lived request.
- Scope: Upload flow, orchestration, job state, progress UI, retries, timeouts, temporary storage, and future public API behavior.
- Implementation: pending
- Recorded against HEAD: not applicable
- Supersedes: none
- Evidence: Analysis-execution model selected during the current design interview.
- Privacy waivers: none

## DEC-0023 — Return an inconclusive partial result when a classifier is unavailable

- Date: 2026-10-20
- Owner: shared
- Status at record: active
- Decision: Allow trusted definitive provenance to decide a result independently, but require both selected probabilistic classifiers for a combined score and return inconclusive with partial-analysis details when either remains unavailable after bounded retries.
- Rationale: A combined probability must not be emitted from an evidence set different from the one used to calibrate it, and provider failure should remain visible to consumers.
- Scope: Job completion rules, retry policy, score emission, partial-result states, provider health handling, and result-page explanations.
- Implementation: pending
- Recorded against HEAD: not applicable
- Supersedes: none
- Evidence: Provider-failure behavior selected during the current design interview.
- Privacy waivers: none

## DEC-0024 — Expire anonymous result links after 24 hours

- Date: 2026-10-20
- Owner: user
- Status at record: active
- Decision: Make each anonymous analysis report retrievable through an unguessable token for no more than 24 hours, without retaining the uploaded image or a thumbnail.
- Rationale: A short private retrieval window supports asynchronous use while remaining consistent with the limited derived-data retention policy.
- Scope: Result storage, access tokens, expiration, download behavior, caching, and privacy disclosures.
- Implementation: pending
- Recorded against HEAD: not applicable
- Supersedes: none
- Evidence: Anonymous report-retention policy selected during the current design interview.
- Privacy waivers: none

## DEC-0025 — Exclude public share links from the initial release

- Date: 2026-10-20
- Owner: shared
- Status at record: active
- Decision: Do not host permanent or public shareable result pages in v1; keep hosted reports private and expiring while allowing users to download a timestamped report with evidence and limitations.
- Rationale: Experimental probabilistic findings should not become durable public accusations after models, evidence, or calibration have changed.
- Scope: Result sharing, report downloads, link access, expiration, safety messaging, and launch feature scope.
- Implementation: pending
- Recorded against HEAD: not applicable
- Supersedes: none
- Evidence: Initial report-sharing policy selected during the current design interview.
- Privacy waivers: none

## DEC-0026 — Target one thousand daily analyses with tenfold headroom

- Date: 2026-10-20
- Owner: shared
- Status at record: active
- Decision: Size the initial system to operate comfortably at 1,000 image analyses per day and scale to 10,000 per day without architectural redesign, using quotas to absorb demand spikes within provider limits.
- Rationale: This envelope supports consumer validation and moderate growth without introducing infrastructure intended for large-scale traffic before demand exists.
- Scope: Capacity planning, queue throughput, database and object storage sizing, concurrency controls, provider quotas, and scaling tests.
- Implementation: pending
- Recorded against HEAD: not applicable
- Supersedes: none
- Evidence: Initial capacity target selected during the current design interview.
- Privacy waivers: none

## DEC-0027 — Target five-to-ten-second analysis completion

- Date: 2026-10-20
- Owner: user
- Status at record: active
- Decision: Target completion of a normal consumer image analysis within 5 to 10 seconds.
- Rationale: The consumer checker should feel responsive despite invoking multiple evidence providers.
- Scope: Provider concurrency, timeout budgets, queue latency, upload limits, progress UI, performance testing, and degraded-result behavior.
- Implementation: pending
- Recorded against HEAD: not applicable
- Supersedes: none
- Evidence: Analysis latency target selected during the current design interview.
- Privacy waivers: none
