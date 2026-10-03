## Hi, I'm Amathziah

![How I build: deterministic where it can be, model where it must be, a human before it ships](./assets/pipeline.svg)

Backend and AI engineer in Delhi. I build systems where the AI part is measured, not assumed, and the infrastructure is reproducible.

Most of my recent work comes back to one idea: **use a model only where judgement is genuinely needed, and prove the rest with code you can audit.** Deterministic rules are instant, free and reproducible — qualification logic, scoring maths and state machines belong there. Models earn their cost on synthesis and language.

### Selected work

**CapitaEdgeX** — my startup · `React` `Node.js` `Supabase` `Gemini` `Docker`

Invoicing and business-assistant platform for small businesses. REST API over invoices, customers, products and expenses; multi-lingual invoice PDF generation; an AI assistant for querying business data; automated email reminders; Supabase for storage and auth. Containerised, with AWS and Render deployment configs.

<sub>Source is private — happy to walk through the architecture.</sub>

**[LeadFlow](https://github.com/amathziah/leadflow)** · `TypeScript` `Node` `PostgreSQL` `Gemini`

B2B lead intelligence platform. Imports companies, enriches them, detects buying signals, scores them against an ICP, researches each account, and drafts evidence-grounded outreach that a human approves before anything sends.

Three things in it I'd defend in a code review:

- **A two-tier eval harness** that runs keyless in CI. On its first run it failed 4 of 18 cases and took qualification precision from **0.64 → 1.00** — substring matching was accepting "Agriculture Software" for a Software ICP, and "Executive Assistant to the CEO" as a CEO.
- **Provenance on every generation.** I found a silent total AI outage: a retired model ID made every call return 404 while each service caught it and returned a template, so the system looked healthy. Responses now carry `generatedBy: llm | fallback`, and a degraded run can't pass as a working one.
- **Send-before-commit delivery.** Outreach reaches `SENT` only after the mail server accepts it, so a failed send never records a delivery that didn't happen.

**[ShopSmart](https://github.com/amathziah/devops)** · `Terraform` `AWS ECS Fargate` `Docker` `GitHub Actions`

Full-stack inventory platform where the deployment pipeline is the point. Terraform provisions ALB, ECS, ECR, S3, IAM and CloudWatch; every push to `main` lints, tests, applies infrastructure, builds and pushes images to ECR, then force-redeploys the ECS service and waits for it to stabilise. Tested at three levels — Jest, Vitest and Playwright E2E.

**[Single-Qubit QNN](https://github.com/amathziah/QCresearch)** · `Qiskit` `Python`

Qiskit reproduction of the single-qubit quantum neural network (data re-uploading classifier) from Pérez-Salinas et al.

**[AgriVision](https://github.com/amathziah/AgriVision-CropYield-SVR)** · `Python` `scikit-learn`

Crop yield prediction using support vector regression.

### Stack

![Tech stack: TypeScript, React, Node.js, PostgreSQL, Python, Docker, Terraform, AWS ECS, GitHub Actions](./assets/stack.svg)
