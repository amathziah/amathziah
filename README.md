## Amathziah J

Backend and AI engineer in Delhi. I work on the part most AI products skip: proving the thing actually does what the README claims.

My default is to **use a model only where judgement is genuinely needed, and prove the rest with code that can be audited.** Qualification rules, scoring maths and state machines are deterministic — instant, free, reproducible, and explainable to whoever has to justify the decision. Models earn their cost on synthesis and language, and everything they produce carries provenance.

![Tech stack](./assets/stack.svg)

---

### CapitaEdgeX — my startup

Invoicing and business-assistant platform for small businesses. REST API over invoices, customers, products and expenses; multi-lingual invoice PDF generation; an AI assistant for querying business data; automated reminders; Supabase for storage and auth. Containerised, with AWS and Render deployment configs.

`React` · `Node.js` · `Supabase` · `Gemini` · `Docker`

<sub>Private source — happy to walk through the architecture.</sub>

---

### [LeadFlow](https://github.com/amathziah/leadflow) — measured AI, not assumed

Lead intelligence pipeline: enrich, detect buying signals, qualify against an ICP, score, research, draft outreach, hold it at a human approval gate.

The engineering worth discussing:

**I built the eval harness, and it failed my own code.** First run: 4 of 18 cases failed at **0.64 precision**. Substring matching accepted "Agriculture Software" for a Software ICP and "Executive Assistant to the CEO" as a decision maker. Token-aware matching took it to **1.00** across 20 cases, 5 adversarial. Tier 1 is a pure function — no DB, no network, no key — so it runs in CI on every push.

**Then it caught a worse one.** Tier 2 reported a flawless 100% grounding, 0% fluff. The numbers were real and the conclusion was wrong: every model call had been 404ing for weeks after Google retired the pinned model ID, each service was silently degrading to a template, and the suite was scoring those templates. [**Full postmortem**](https://github.com/amathziah/leadflow/blob/main/docs/POSTMORTEM-silent-model-outage.md) — the root cause is one line; the interesting part is the three layers that kept a total outage invisible.

**A state machine that refuses to lie.** Outreach reaches `SENT` only after the mail server accepts it. Failed send, missing recipient, unconfigured SMTP — the message stays `APPROVED` and the error surfaces. The system never records a delivery that did not happen.

`TypeScript` · `Node` · `PostgreSQL` · `Prisma` · `Gemini`

---

### [ShopSmart](https://github.com/amathziah/devops) — push to production, nothing by hand

Inventory platform used as the payload for a reproducible delivery path. 25 Terraform resources; no console-clicked state anywhere. A push to `main` lints, tests, plans and applies infrastructure, builds both images, pushes to ECR, force-redeploys the ECS service and blocks until stable. Tested at three levels — Jest, Vitest, Playwright.

IAM is scoped to `GetObject`/`PutObject` on **exactly one object**, not the bucket. Encryption and versioning on, public access blocked.

The README documents the weaknesses as plainly as the strengths: persistence is a single JSON object read-modify-written with no compare-and-swap, so concurrent writers lose updates. Both fixes are written up — `If-Match` conditional writes, or DynamoDB.

`Terraform` · `AWS ECS Fargate` · `Docker` · `GitHub Actions`

---

### [Single-Qubit QNN](https://github.com/amathziah/QCresearch)

Qiskit reproduction of the data re-uploading classifier from Pérez-Salinas et al.

---

**[LinkedIn](https://www.linkedin.com/in/amathziah-j-832646214/)** · Delhi, India
