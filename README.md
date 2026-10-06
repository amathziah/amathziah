## Amathziah J

**Backend and AI engineer** in Delhi. I build systems that can prove they work.

Most AI products *assert* quality. I measure it — and the measurements have caught my own bugs twice: a **precision defect in my matching logic**, and a **total model outage the system was reporting as healthy**.

The rule I work by: **use a model only where judgement is genuinely needed.** Qualification rules, scoring maths and state machines stay deterministic — instant, free, reproducible, and explainable to whoever has to defend the decision. Models earn their cost on synthesis and language, and everything they generate carries provenance.

![Tech stack](./assets/stack.svg)

---

### CapitaEdgeX — my startup

Invoicing and business-assistant platform for small businesses. REST API over invoices, customers, products and expenses · **multi-lingual invoice PDF generation** · AI assistant for querying business data · automated reminders · Supabase storage and auth. Containerised, with AWS and Render deploy configs.

`React` · `Node.js` · `Supabase` · `Gemini` · `Docker`
<sub>Private source — happy to walk through the architecture.</sub>

---

### [LeadFlow](https://github.com/amathziah/leadflow) — measured AI, not assumed

Enrich → detect buying signals → qualify against an ICP → score → research → draft outreach → **human approval gate**.

**The eval suite failed my own code.** First run: 4 of 18 cases, **0.64 precision**. Substring matching was accepting *"Agriculture Software"* for a Software ICP and *"Executive Assistant to the CEO"* as a decision maker. Token-aware matching took it to **1.00** across 20 cases, 5 adversarial. Tier 1 is a pure function — **no database, no network, no API key** — so it runs in CI on every push.

**Then it caught something worse.** Tier 2 reported a flawless **100% grounding, 0% fluff**. The numbers were real and the conclusion was wrong: every model call had been **404ing for weeks** after Google retired the pinned model ID, each service was silently degrading to a template, and the suite was scoring those templates. **A metric that cannot tell a working system from a broken one is not a metric.** → [**full postmortem**](https://github.com/amathziah/leadflow/blob/main/docs/POSTMORTEM-silent-model-outage.md)

**A state machine that refuses to lie.** Outreach reaches `SENT` only once the mail server accepts it. Failed send, missing recipient, unconfigured SMTP — it stays `APPROVED` and the error surfaces. **The system never records a delivery that did not happen.**

`TypeScript` · `Node` · `PostgreSQL` · `Prisma` · `Gemini`

---

### [ShopSmart](https://github.com/amathziah/devops) — push to production, nothing by hand

**25 Terraform resources**, zero console-clicked state. One run: lint, test, plan, apply, build both images, push to ECR, redeploy ECS, block until stable. Tested at three levels — **Jest, Vitest, Playwright**.

IAM is scoped to **exactly one S3 object**, not the bucket. Encryption and versioning on, public access blocked.

The README states the weaknesses as plainly as the strengths: persistence is a single JSON object with no compare-and-swap, so **concurrent writers lose updates** — both fixes written up. Deploys are manual-only, after a documentation commit once stood up a load balancer and started billing by the hour.

`Terraform` · `AWS ECS Fargate` · `Docker` · `GitHub Actions`

---

### [Single-Qubit QNN](https://github.com/amathziah/QCresearch)

Qiskit reproduction of the **data re-uploading classifier** from Pérez-Salinas et al.

---

---

### Contribution graph

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amathziah/amathziah/output/snake-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/amathziah/amathziah/output/snake-light.svg">
  <img alt="Contribution snake" src="https://raw.githubusercontent.com/amathziah/amathziah/output/snake-dark.svg">
</picture>

---

<a href="https://www.linkedin.com/in/amathziah-j-832646214/"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>&nbsp;&nbsp;<a href="mailto:jamathziah.23csai@nst.rishihood.edu.in"><img src="https://img.shields.io/badge/Email-0F0F18?style=for-the-badge&logo=gmail&logoColor=A78BFA" alt="Email"></a>

Delhi, India
