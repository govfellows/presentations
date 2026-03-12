# DMV AI in Production: What Could Your Department Do With These Tools?

Governor's Innovation Fellows Program

**Core Thesis:** DMV has 6 AI systems in production saving thousands of staff hours annually. Every Fellowship department has problems these proven patterns already solve — the question is which ones fit your shop.

March 2026 | Based on DMV Innovation Tour, January 30, 2026

---

## Before You Read: How to Use This Deck

This deck is **prep material for the March 20 Fellows meeting.** Here's the plan:

1. **Now** — Read this deck. Find your department. Look at which DMV tools apply.
2. **Before March 20** — Have one conversation with someone in your shop. Ask: "If we had this, what would change?"
3. **March 20 meeting** — Bring your ideas. We'll discuss as a group.
4. **After the meeting** — A formal survey will capture everyone's ideas in writing.

This deck includes AI-generated suggestions for how DMV's tools might apply at each department. **Some will be on target; others will miss the mark entirely.** Only you and your department know where these patterns actually fit. That's the point — we need your expertise, not more AI guesswork.

**Skip to your department:** Use the left-hand navigation to jump to "Your Department at a Glance."

---

## Why This Matters

California DMV is running **six distinct AI/automation systems** in production — more than most state departments have even piloted.

The critical pattern: DMV uses AI as a **decision-support layer** (human stays in the loop), not full automation. This approach:

- Requires no new legislation
- Has survived legal challenge (Personalized Plates: zero lawsuits since GenAI implementation)
- Produces measurable, auditable results

The [Governor's Innovation Fellows Program](https://innovation.ca.gov/) puts 21 Fellows across **15 departments in 9 agencies** — every one of which has a direct opportunity to benefit from DMV's proven approach.

---

## 3 Focus Areas for March 20

For this meeting, we're focusing on the **three DMV systems with the broadest applicability** across Fellowship departments:

| Focus Area | What DMV Built | Why It Matters to You |
|-----------|---------------|----------------------|
| **Miles Chatbot** | Voice & chat AI handling **13.77M calls/year** — 49% now fully self-service | Every department has a call center or help desk. What would *your* Miles answer? |
| **RADV Document Verification** | OCR + ML auto-verifies **62% of documents** — saving **22,050 hours/year** (28 FTE) | Every department processes paper. Which forms eat the most staff time? |
| **MyDMV Identity Verification** | Multi-tier identity proofing at **90-95% success** (up from 35-40%) | Every department with online accounts needs identity verification. Where does proving identity create friction? |

DMV also has 3 additional systems covered later in this deck: Service Advisor (AI web search), Disaster Recovery App (mobile field ops), and GenAI for Personalized Plates (content review). Browse those for additional ideas.

---

## The Master Pattern: AI Assists, Humans Decide

Every one of DMV's 6 AI systems follows the same architecture:

1. **AI processes** — Extracts, classifies, recommends, routes
2. **Human decides** — Reviews flagged items, makes final call
3. **Automation executes** — Carries out the approved action

This isn't a coincidence. It's a deliberate design choice that:

- **Satisfies legal requirements** — Human accountability for decisions
- **Builds staff trust** — AI augments, doesn't replace
- **Survives scrutiny** — Personalized Plates has had zero lawsuits since implementation
- **Improves over time** — ML learns from human corrections

**This is the pattern other departments should look at.** Not "AI replaces workers" — but "AI handles the 60-90% that's routine so workers can focus on the cases that actually need judgment."

---

## The 6 AI Systems in Production

| # | System | AI Type | Launched | Key Metric |
|---|--------|---------|----------|------------|
| 1 | **Miles Chatbot** — Voice & Chat | NLP → GenAI | Ongoing | 13.77M calls/year handled |
| 2 | **RADV** — Document Verification | OCR/ICR + ML | 2020 | 5.4M docs/year, 62% automated |
| 3 | **MyDMV** — Identity Verification | Multi-tier Auth + Biometrics | Active | 90-95% verification success |
| 4 | **Service Advisor** — Web Search | Semantic Search | Active | 1M+ queries/year |
| 5 | **GenAI Plates** — Content Review | GenAI + RPA | Nov 2022 | 90% auto-processed, 0 lawsuits |
| 6 | **Disaster Recovery App** — Field Ops | GIS Mobile App | Active | 195 vehicles mapped (Sacramento region) |

Each system follows the same philosophy: **AI assists, humans decide.**

---

## Focus 1: Miles Chatbot — Voice & Chat AI

**Presenter:** Sonia Huestis | **Technology:** NLP chatbot evolving toward GenAI conversational bot

### Scale: 13.77 Million Calls in 2025

:::chart doughnut
| Channel | Calls (M) |
|---------|-----------|
| Self-Service | 6.8 |
| Requested Agent | 5.6 |
| Full Message | 1.4 |
:::

The bot deflected **6.8M calls** to self-service in 2025 (up from 6.0M in 2024) — a 13% increase in automation without adding staff.

Top call reasons: VR Renewal (13%), Title Transfer (5%), DL Renewal (5%), Drive Test Appointments (4%).

---

## Miles Chatbot: Evolution Roadmap

The roadmap shows a clear pattern from **rule-based → semantic → generative → predictive:**

| Date | Milestone | What Changes |
|------|-----------|-------------|
| March '25 | **Content Cleanup** | Reduce QnA utterance noise — fewer dead-end responses |
| April '25 | **VR Status** | Customers check vehicle registration status via bot |
| Sept '25 | **Semantic Search** | Bot understands *meaning and context*, not just keywords |
| Nov '25 | **DL Status** | Customers check driver's license renewal status via bot |
| Dec '25 | **GenAI Convo Bot** | New knowledge base + content safety guardrails |
| Q1-Q2 '26 | **Predictive Caller** | Bot determines caller intent *before* connecting |
| Q1-Q2 '26 | **Title Transfer** | Full self-service title transfer via bot |

**Key takeaway for other departments:** You don't have to start at GenAI. Enter the roadmap at whatever stage matches your current maturity — even a keyword QnA bot that handles the top 5 call reasons creates immediate value.

---

## Focus 2: RADV — Real ID Automated Document Verification

**Presenter:** Adrian Monteon | **Technology:** [ABBYY](https://www.abbyy.com/) OCR/ICR + Machine Learning

### How It Works

Citizens upload identity documents (birth certificates, passports, EAD cards, I-94s) through the [online portal](https://www.dmv.ca.gov/portal/). The ABBYY engine:

1. **Extracts** printed text and handwritten entries via OCR/ICR
2. **Validates** extracted data against DMV's database
3. **Auto-approves** documents that pass (~62%)
4. **Routes failures** to a human technician for manual review

### Five-Year Average Savings

- **Time saved:** 22,050 hours/year
- **Staff equivalent:** 28 FTE/year
- **Documents processed:** Millions monthly

---

## RADV: Automation Rate Climbing Year Over Year

:::chart bar
| Year | Automated | Human Touch |
|------|-----------|-------------|
| 2021 | 2.9 | 2.5 |
| 2022 | 2.6 | 2.1 |
| 2023 | 3.1 | 2.2 |
| 2024 | 2.8 | 1.7 |
| 2025 | 3.3 | 2.1 |
:::

Automation rate rose from **53% in 2021 to 62% in 2025** — driven by machine learning improvements, not just volume growth. The Digital Imaging and Archiving extension reached **75% automation** for internal form processing (309K docs in 2025).

---

## Focus 3: MyDMV — Identity Management & Automation

**Presenter:** Stefan Schoy | **Technology:** Multi-tier automated identity verification via [MyDMV](https://mydmv.dmv.ca.gov/) + biometric exploration

### The Problem → The Fix

| | Before | After |
|---|--------|-------|
| **Approach** | Single verification attempt | Two-tier (Level 1 → Level 2 fallback) |
| **Success Rate** | 35-40% | **90-95%** |
| **Failure Routing** | All failures → call center | Only double-failures → agent |
| **Document Flexibility** | Rigid single pathway | Multiple verification pathways |

### High-Risk Application Protections

For sensitive operations (phone number reset, replacement DL), the system adds external identity verification services — validating against third-party databases *in addition to* DMV records.

### Future: Biometric Verification

DMV is exploring selfie + camera comparison against the DL photo on file — for both [MyDMV](https://mydmv.dmv.ca.gov/) account creation and [CA DMV Wallet](https://www.dmv.ca.gov/portal/ca-dmv-wallet/) (mDL) issuance. Same face = verified identity = credential issued.

---

## Your Department at a Glance — GovOps Agency

### CDT (Dept of Technology) — Jennifer Uyeda Issertell

| DMV Tool | What This Could Look Like |
|----------|--------------------------|
| **Miles-style Chatbot** | Statewide IT help desk bot — password resets, service tickets, system status. CDT's ServiceNow platform already has structured data; a bot layer on top could deflect 40%+ of routine calls. |
| **Identity Verification** | CDT could offer identity proofing as a **shared service** for all state departments. One implementation, every department benefits. The EDD fraud crisis proved what happens without this. |

**Your question:** *CDT serves every department in the state. If you could automate the top 5 help desk requests, what would they be? And what would a statewide identity verification service save your department users?*

### DGS (General Services) — Lorna Brisco

| DMV Tool | What This Could Look Like |
|----------|--------------------------|
| **Miles-style Chatbot** | Procurement support bot — vendor bid status, contract questions. DGS handles thousands of "Where's my PO?" inquiries; a status-check bot could deflect significant volume. |

**Your question:** *What are the top 5 questions vendors and departments ask DGS over and over? Those are your Miles candidates.*

### CDTFA (Tax & Fee Admin) — Jeremiah Oakden

| DMV Tool | What This Could Look Like |
|----------|--------------------------|
| **Miles-style Chatbot** | Taxpayer inquiries — "When is my return due?" "What's my balance?" These are the exact same query types Miles handles for DMV, just with tax data. |
| **Document Verification** | Tax return processing — sales tax returns, exemption certificates. CDTFA already digitizes returns; adding ML validation could flag mismatches before they reach auditors. |

**Your question:** *What percentage of CDTFA call center volume is simple status checks? And which return types have the most data-entry errors that auditors catch manually?*

---

## Your Department at a Glance — Health & Human Services

### DDS (Developmental Services) — Henri Aghaei Baradaran

| DMV Tool | What This Could Look Like |
|----------|--------------------------|
| **Document Verification** | Regional center intake — ~460K clients submit eligibility paperwork. Automated verification could speed intake from weeks to days for standardized forms. |

**Your question:** *How long does intake document processing take at regional centers today? Which document types cause the most rework?*

### DCSS (Child Support) — Bryanna McAdams

| DMV Tool | What This Could Look Like |
|----------|--------------------------|
| **Miles-style Chatbot** | DCSS already has "Customer Connect 24/7" — but DMV's semantic search + GenAI roadmap shows the upgrade path to context-aware responses. |
| **Document Verification** | Child support order verification — income declarations across 47 county agencies. Each county submits slightly different formats; ML normalization is the high-value target. |
| **Identity Verification** | Parent identity verification for the child support portal. DCSS serves 1.2M cases across 47 counties — reliable identity proofing reduces fraud and call center burden. |

**Your question:** *What's the most common reason a parent contacts DCSS? And across 47 counties, how much staff time goes to reconciling different document formats?*

### OTSI/CalHHS — Kattya Trinh

| DMV Tool | What This Could Look Like |
|----------|--------------------------|
| **Miles-style Chatbot** | Medi-Cal questions, benefit status, provider lookup. CalHHS serves millions — a chatbot reduces the burden on county eligibility workers. |
| **Identity Verification** | Medi-Cal eligibility verification for 14M+ beneficiaries. CalHHS already partners with Login.gov; DMV's two-tier model would add a state-specific fallback layer. |

**Your question:** *How many Medi-Cal eligibility calls could be handled by a bot that can authenticate and return status? Where does identity verification create the most friction for beneficiaries?*

---

## Your Department at a Glance — Transportation Agency

### CHP (Highway Patrol) — Lt. Marc Peachey

| DMV Tool | What This Could Look Like |
|----------|--------------------------|
| **Miles-style Chatbot** | Accident report status, permit questions, commercial vehicle requirements. CHP handles significant public-facing call volume — status checks are prime bot territory. |

**Your question:** *What are CHP's top 10 public call reasons? How many are simple status checks or FAQ lookups that don't require an officer?*

### Caltrans — Ben Bressette

| DMV Tool | What This Could Look Like |
|----------|--------------------------|
| **Miles-style Chatbot** | Project status, encroachment permits, traffic data inquiries. Caltrans.ca.gov is one of the state's highest-traffic sites — an AI search layer would serve millions of visitors. |

**Your question:** *What are the top queries on caltrans.ca.gov? How much call center time goes to project status checks or permit questions that have straightforward answers?*

---

## Your Department at a Glance — Natural Resources & Environment

### DWR (Water Resources) — Nikki Hatcher

| DMV Tool | What This Could Look Like |
|----------|--------------------------|
| **Document Verification** | Water right applications involve massive paper submissions. DWR has 7M+ historical documents — automated extraction could feed directly into CalWATRS. |

**Your question:** *How many water right applications does DWR process annually? Which document types in those applications are most standardized (best candidates for automation)?*

### SWRCB (Water Board) — Brent Vanderburgh

| DMV Tool | What This Could Look Like |
|----------|--------------------------|
| **Document Verification** | Water rights division has paper records dating to the 1800s. The UPWARD initiative ($60M) is digitizing; AI verification is the next step in that chain. |

**Your question:** *Which water rights forms have the highest error rates? Where in the UPWARD digitization pipeline would automated verification create the most value?*

### OEHHA — Kannan Krishnan

| DMV Tool | What This Could Look Like |
|----------|--------------------------|
| **Miles-style Chatbot** | Proposition 65 chemical hazard lookup — businesses search the Prop 65 list thousands of times daily. An AI search that interprets plain-English queries ("Is BPA in baby bottles covered?") instead of requiring exact chemical names. |

**Your question:** *How many Prop 65 inquiries does OEHHA handle? What are the most common questions businesses ask that have clear, lookup-based answers?*

### CARB (Air Resources) — Christina Marin-Fitzhugh

| DMV Tool | What This Could Look Like |
|----------|--------------------------|
| **Miles-style Chatbot** | ZEV compliance, emission regulations, Cap-and-Invest program questions. Fleet operators need to understand complex compliance pathways — a guided advisor replaces the "call us" experience. |

**Your question:** *What are the top compliance questions CARB receives from fleet operators and businesses? How much staff time goes to answering questions that have standardized answers?*

### Natural Resources Agency — Elizabeth Betancourt

| DMV Tool | What This Could Look Like |
|----------|--------------------------|
| **Document Verification** | Environmental review document screening — EIRs can run 500+ pages. AI-assisted summarization and issue flagging could dramatically reduce reviewer workload. |

**Your question:** *How many environmental review documents does your team process annually? What's the average review time, and which sections consume the most attention?*

---

## Your Department at a Glance — Military, Corrections & Other

### CDCR (Corrections) — Samantha Kissane & Chris Siino

| DMV Tool | What This Could Look Like |
|----------|--------------------------|
| **Document Verification** | Inmate records, transfer paperwork, parole documentation — CDCR processes thousands of classification chronos (Form 128-B) monthly, many still handwritten. |
| **Identity Verification** | Inmate and officer identification at kiosks. DMV's biometric approach could transform check-in/check-out processes across facilities. |

**Your question:** *Which CDCR forms are still handwritten? What's the volume of classification documents processed monthly? Where would faster identity verification — for staff or inmates — have the biggest operational impact?*

### CMD (Military Dept) — Jai London & SSgt Kelton Pisano

| DMV Tool | What This Could Look Like |
|----------|--------------------------|
| **Document Verification** | Personnel action forms, deployment orders. Military paperwork is highly standardized (DD-214s, SF-180s) — ideal for automated verification with near-zero customization needed. |

**Your question:** *Which personnel or deployment forms are the most time-consuming to process? Where do document errors cause the most downstream delays?*

### CA Air National Guard — SMSgt Blake Carter

| DMV Tool | What This Could Look Like |
|----------|--------------------------|
| **Document Verification** | Personnel action forms and deployment orders. The A1 Connect platform already handles some document workflows — AI verification could extend its capabilities. |

**Your question:** *What document processing does A1 Connect handle today, and where are the gaps? Which forms still require manual review that could be automated?*

### LCI (Land Use & Climate) — Will Robinson

| DMV Tool | What This Could Look Like |
|----------|--------------------------|
| **Miles-style Chatbot** | CEQA guidance is notoriously complex. An AI advisor for CEQA requirements, housing element compliance, and climate adaptation resources could cut the learning curve for project applicants. |

**Your question:** *What are the most common CEQA questions LCI receives? How many hours per week does staff spend answering questions that have standard, policy-based answers?*

### CA Volunteers — Molly Linares

| DMV Tool | What This Could Look Like |
|----------|--------------------------|
| **Miles-style Chatbot** | Volunteer matching and program questions. The ServiceForce database + chatbot = self-service volunteer placement. Lower call volume makes this a natural low-risk pilot environment. |

**Your question:** *How do volunteers currently find opportunities — and where does that process break down? What are the top 5 questions volunteers or organizations ask?*

---

## Questions to Bring to the March 20 Meeting

Before the meeting, try to find out:

1. **If your department had a Miles, what would people ask it?** Think about your call center, help desk, or front counter — what are the top 5 questions that come in over and over?

2. **What's your department's highest-volume paper form?** Roughly how many per month? Is it still partially handwritten or fully digital? How much staff time goes to processing it?

3. **Where does proving identity create friction?** For the public trying to access your services online — or for staff logging into systems. Where do people get stuck?

4. **If you could automate one repetitive review or intake task, what would it be?** The one where staff look at the same kind of document hundreds of times and make the same determination.

You don't need formal answers. A five-minute conversation with the right person in your shop will surface more than a week of desk research.

---

## What Happens Next

| Phase | What | When |
|-------|------|------|
| **Prep** | Read this deck, talk to your department | Now through March 20 |
| **Discuss** | Group discussion at monthly meeting | March 20 |
| **Capture** | Formal survey to memorialize ideas | After the meeting |
| **Discover** | Deep-dive session with DMV subject matter experts | TBD based on survey results |
| **Scope** | IT, security, costs, and implementation planning | After discovery — not before |

We're deliberately keeping the conversation at the **business-need level** for now. The technical details, security reviews, and cost estimates come later — once we know which patterns have the strongest fit across departments. First we figure out *what*, then we figure out *how*.

---

## Additional Reference: Service Advisor — AI-Driven Web Search

**Presenter:** Randolph L. Fernandez-Gonzalez | **Technology:** Semantic search + guided form-filling assistant

Integrated into [dmv.ca.gov](https://www.dmv.ca.gov/) at the **three highest-traffic touchpoints:** homepage search, site-wide search, and the [appointments page](https://www.dmv.ca.gov/portal/appointments/).

:::chart bar
| Query Category | Queries (K) |
|---------------|-------------|
| Real ID | 258 |
| Driver Permits | 209 |
| Release of Liability | 155 |
| Change of Address | 143 |
| Title Transfers | 121 |
| Registration | 109 |
| Appointments | 102 |
:::

---

## Service Advisor: Key Capabilities

### Not Just Search — It's an AI Assistant

- **Contextual answers** — Returns structured guidance, not just links. Searching "statement of facts" identifies the exact form (REG 256), explains all 6 uses, and offers a guided Form Filler.

- **Form Filler integration** — Walks users step-by-step through DMV forms. Enter your license plate, answer questions, and it generates a completed PDF.

- **Scam detection** — Recognizes known scam reference numbers and *immediately* surfaces fraud alerts: "The DMV will never ask for personal or financial information by text."

- **[mDL](https://www.dmv.ca.gov/portal/ca-dmv-wallet/) Q&A assistant** — Handles mobile driver's license questions with corrective actions when something goes wrong.

- **Adaptable** — Same interface handles procedural guidance (Notice of Transfer walkthrough) and real-time crisis response (scam alerts).

**This is the most universally transferable pattern.** Every department has a website. Every website has a "How do I...?" problem.

---

## Additional Reference: GenAI + Intelligent Automation for Personalized Plates

**Presenter:** Angela Marbray | **Technology:** Generative AI (content review) + RPA (plate assignment)

### The Origin Story

A 2020 lawsuit ([*Ogilvie v. Steve Gordon*](https://casetext.com/case/ogilvie-v-gordon-3)) exposed that plate configuration decisions were **subjective and inconsistent** across reviewers. The numbers told the story:

- **167,000** orders/year (~668/day)
- Only **4 reviewers** + 5 assignment staff
- **36,000 plate backlog**
- Up to **9 months** wait time
- **Inconsistent** approve/deny decisions

---

## Personalized Plates: The AI Solution

### Two-Part Fix

1. **Generative AI (Nov 2022):** Reviews plate configurations for offensive/inappropriate content. Makes approve/deny recommendations. Eliminated human bias and created consistency.

2. **Intelligent Automation (July 2023):** Assigns approved plates to vehicles automatically. Runs 24/7 — no breaks, no sick days, works beyond business hours.

### End-to-End Flow

**Intake** → **GenAI Assist** → **Staff Review** → **IA Assist** → **Fulfillment**

Online, Mail, Field Office, AAA → Machine review, flags & routing → **Final human decision** → Assigns plates to vehicles → [CALPIA](https://www.calpia.ca.gov/) Manufacturing

### Results

| Metric | Result |
|--------|--------|
| **IA processing rate** | 90% of all plate assignments |
| **AI approval rate** | 90% of AI recommendations confirmed by staff |
| **Wait time** | 2-4 months (was 9 months) — **50% reduction** |
| **Lawsuits** | **0** since implementation |

The human-in-the-loop design is why there are zero lawsuits. GenAI *recommends*, staff *decides*.

---

## Additional Reference: Disaster Recovery App — Mobile Field Investigation

**Presenter:** Amy Burks | **Technology:** GIS-based mobile application for field data collection

### Real-World Application

Used by DMV investigators to locate and document vehicles destroyed in wildfires and other natural disasters. The mobile app:

- Maps investigation clusters using GIS (195 vehicles in Sacramento region alone)
- Enables on-site data collection via iPad
- Tracks investigation status in real-time
- Syncs field data with central databases

### Field Operations

Investigators physically locate burned vehicles at disaster sites — crawling under wreckage to read VINs, photographing damage, recording GPS coordinates — all feeding back through the app.

Less "AI" in the traditional sense, more **intelligent field data collection** — but the GIS clustering, mobile-first workflow, and real-time sync represent a model for any department with field operations.

---

## DMV Contacts & Your Internal Bridge

### DMV Innovation Team

| Name | Area | Email |
|------|------|-------|
| Adrian Monteon | Document Processing (RADV) | adrian.monteon@dmv.ca.gov |
| Sonia Huestis | Miles Chatbot | sonia.huestis@dmv.ca.gov |
| Randolph L. Fernandez-Gonzalez | Service Advisor | randolph.gonzalez@dmv.ca.gov |
| Stefan Schoy | MyDMV Identity | stefan.schoy@dmv.ca.gov |
| Amy Burks | Disaster Recovery App | amy.burks@dmv.ca.gov |
| Angela Marbray | GenAI Personalized Plates | angela.marbray@dmv.ca.gov |

### Your Internal Bridge

**Liyuan Guo** — DMV's own Innovation Fellow (EEO Officer) — is already in Cohort 1. She can serve as the liaison between DMV's innovation teams and Fellows from other departments.

---

## Key Takeaways

1. **Human in the loop is non-negotiable.** Every DMV AI system keeps a human making the final decision. The Personalized Plates flow (GenAI recommends → Staff decides → IA executes) survived legal challenge with zero lawsuits. That's your template.

2. **Identity verification is the biggest multiplier.** DMV proved 90-95% success at scale. If CDT offers this as a shared service, every department skips years of work.

3. **The chatbot roadmap is a replicable playbook.** Keyword QnA → Semantic Search → GenAI → Predictive. Enter at whatever stage matches your maturity.

4. **Start with the easiest win for your department.** Every department has a website, a call center, or a pile of paper forms. Pick the one that causes the most pain and look at how DMV addressed the same problem.

5. **Don't start from scratch.** That's the whole point. DMV has proven patterns in production — the opportunity is to adapt what works, not reinvent it.
