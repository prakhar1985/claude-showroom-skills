---
layout: default
title: Create Demo
parent: Skills
nav_order: 3
description: "Create presenter-led demos with Know/Show methodology"
---

# Create Presenter Demos
{: .no_toc }

Guided workflow for creating presenter-led demonstrations that meet Red Hat quality standards.
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## What It Does

The `/create-demo` skill guides you through creating presenter-led demonstrations with:

✅ **Know/Show structure** (business context → technical demonstration)
✅ **Sequential questioning** (one question at a time, wait for answer)
✅ **Automatic file generation** (index, overview, details, modules)
✅ **Business impact focus** (ROI, metrics, competitive advantages)
✅ **Presenter guidance** (talk tracks, timing, Q&A preparation)
✅ **Mandatory conclusion** with consolidated references

---

## When to Use

Create presenter demos when you need:

- **Customer-facing demonstrations** for sales or field teams
- **Business value presentations** (not hands-on learning)
- **Executive briefings** with technical deep-dives
- **Competitive showcases** highlighting Red Hat advantages
- **Partner enablement** content for channel partners

{: .note }
> For learner-focused workshops, use [`/create-lab`](create-lab) instead. Demos are presenter-focused; workshops are learner-focused.

---

## How Demos Differ from Workshops

| Aspect | Workshop (`/create-lab`) | Demo (`/create-demo`) |
|--------|-------------------------|---------------------|
| **Audience** | Learners (hands-on) | Viewers (presenter-led) |
| **Structure** | Learning objectives + exercises | Know (business) + Show (technical) |
| **Verification** | Mandatory checkpoints | Optional (presenter handles live) |
| **Troubleshooting** | Required for learners | Optional (presenter expertise assumed) |
| **Focus** | Skill building | Business value + capabilities |
| **Time** | 30-45 min per module | 10-15 min per module |
| **Outcome** | Learner can do it themselves | Viewer understands value proposition |

---

## Before You Start

Have these materials ready:

- **Business scenario** (what customer problem does this solve?)
- **Value proposition** (why Red Hat, why now?)
- **Competitive differentiators** (how we're better than alternatives)
- **Target audience** (CxO, IT leaders, technical teams?)
- **Demo environment** details (live cluster, pre-recorded, hybrid)
- **Success metrics** (quantified business impact)

{: .tip }
> Demos lead with business value, not features. Prepare ROI data and customer success stories before starting.

---

## How to Use

### Start New Demo Series

```bash
# Navigate to your Showroom project
cd ~/showroom-my-demo

# Start Claude Code
claude

# Create first module
/create-demo --new
```

### Continue Existing Demo

```bash
# In same project directory
claude

# Add another module
/create-demo --continue
```

---

## The Workflow

The skill uses a **12-step sequential workflow** similar to `/create-lab`, but with demo-specific questions.

### Step 0: Parse Command Arguments

**What happens:**
- Detects `--new` or `--continue` flag
- If no flag, asks whether this is a new demo or continuation

**Your input:**
- Nothing (if you used flags)
- OR answer: "This is a new demo" or "Continue existing demo"

---

### Step 1: Determine Demo Status

**What happens:**
- For new demos: Proceeds to Step 2
- For continuations: Detects existing modules, skips to Step 3

**Automatic detection:**
```
Scanning content/modules/ROOT/pages/...
Found existing modules:
  ✓ 00-index.adoc
  ✓ 01-overview.adoc
  ✓ 02-details.adoc
  ✓ 03-module-01-value-prop.adoc

Detected: Continuation (will create module 04)
```

---

### Step 2: Plan Overall Demo Story (New Only)

**What's asked:**
1. **Demo title**: What product/capability are you showcasing?
2. **Customer scenario**: What real-world problem are you solving?
3. **Business impact**: What quantified results can customers expect?
4. **Presentation arc**: How will the story unfold across modules?
5. **Target audience**: Who is the decision maker?

**Example answers:**
```
Title: "Accelerating AI Model Deployment with Red Hat OpenShift AI"
Customer scenario: "Global bank needs to deploy fraud detection models
                   faster while meeting regulatory compliance requirements"
Business impact: "Reduce model deployment time from weeks to hours,
                 improve fraud detection accuracy by 25%, ensure SOC2 compliance"
Presentation arc: "Module 1: Business challenge → Module 2: Solution demo →
                   Module 3: Results and ROI"
Target audience: "VP of Technology, Chief Data Officer, ML Engineering leads"
```

{: .note }
> The skill remembers this story for all subsequent modules. You don't need to repeat it.

---

### Step 2.5: AgnosticV Catalog (Optional)

**What's asked:**
- "Are you creating this for Red Hat Demo Platform (RHDP)?"

**If yes:**
- Skill helps generate `catalog.yaml` for AgnosticV
- Extracts variables from catalog for use in content
- Generates UUIDs for catalog entries

**If no:**
- Skips catalog generation
- Uses placeholder attributes instead

{: .tip }
> Most users select "No" unless deploying to RHDP. You can always add catalog later.

---

### Step 3: Gather Module-Specific Details

**What's asked:**
1. **Module title**: What will you demonstrate in this section?
2. **Know section**: What business context must viewers understand?
3. **Show section**: What will the presenter demonstrate?
4. **Key messages**: What 3-5 takeaways should viewers remember?
5. **Estimated time**: How long will this module take to present?
6. **Competitive advantages**: How is Red Hat better than alternatives?

**Example answers:**
```
Module title: "Deploying AI Models at Scale"

Know section:
  - Traditional ML deployment takes 2-3 weeks per model
  - Regulatory requirements delay production releases
  - Manual deployment causes configuration drift

Show section:
  - Deploy fraud detection model in 5 minutes
  - Demonstrate automated compliance checks
  - Show real-time monitoring and rollback capabilities

Key messages:
  - Red Hat OpenShift AI reduces deployment time by 90%
  - Built-in compliance automation ensures SOC2/GDPR adherence
  - GitOps-based deployment eliminates configuration drift
  - Enterprise support de-risks production ML workloads

Time: 10-15 minutes
Competitive advantages:
  - AWS SageMaker requires vendor lock-in (Red Hat is hybrid cloud)
  - Azure ML lacks on-premises option (Red Hat supports edge)
  - Databricks has no Kubernetes integration (Red Hat native K8s)
```

---

### Steps 4-7: Content Enhancement

**Step 4: Dynamic Variables**
- "What variables should be extracted?" (e.g., `{web_console_url}`, `{model_name}`)
- Variables go in `partials/_attributes.adoc`

**Step 5: Diagrams**
- "Will this module include diagrams?" (Yes/No)
- If yes: Describes where images should be placed

**Step 6: Troubleshooting**
- "Should we include troubleshooting section?" (Optional for demos)
- If yes: Documents common issues presenters might encounter

**Step 7: Presenter Notes**
- "What should presenters emphasize?" (Mandatory for demos)
- Talking points, timing cues, audience engagement tips

---

### Step 8: Generate Files

**For first module** (`--new`):
Creates 4 files:

```
00-index.adoc           # Landing page with demo overview
01-overview.adoc        # Customer scenario and business impact
02-details.adoc         # Environment details and prerequisites
03-module-01-*.adoc     # First demonstration module
```

**For continuation** (`--continue`):
Creates 1 file:

```
04-module-02-*.adoc     # Next module in sequence
```

{: .warning }
> Files are written directly to `content/modules/ROOT/pages/`. Back up existing content before running the skill!

---

### Step 10: Update Navigation

**What happens:**
- Automatically updates `content/modules/ROOT/nav.adoc`
- Adds new module to navigation menu
- Maintains proper ordering

**Example nav.adoc update:**
```asciidoc
* xref:00-index.adoc[Demo Home]
* xref:01-overview.adoc[Overview]
* xref:02-details.adoc[Technical Details]
* xref:03-module-01-value-prop.adoc[Module 1: Value Proposition]
* xref:04-module-02-technical-demo.adoc[Module 2: Technical Demo]  ← NEW
```

---

### Step 12: Generate Conclusion Module

**What's asked** (when you're ready to finish):
- "Is this the final module?" (Yes/No)

**If yes:**
- Generates conclusion module (`0X-conclusion.adoc`)
- Consolidates ALL references from all modules
- Includes business impact summary
- Provides call-to-action (next steps for customers)
- Links to Red Hat sales resources and technical documentation

{: .note }
> Conclusion modules are **mandatory** in Red Hat demos. They wrap up the business case and provide clear next steps.

---

## What You Get

### First Module Output (4 Files)

#### `00-index.adoc` (Landing Page)
```asciidoc
= Accelerating AI Model Deployment with Red Hat OpenShift AI

Welcome to this demonstration of Red Hat OpenShift AI capabilities.

== Demo Overview

See how enterprises accelerate AI model deployment while maintaining compliance and governance.

== Business Impact

* Reduce deployment time from weeks to hours
* Improve model accuracy with automated validation
* Ensure regulatory compliance with built-in controls

== Modules

. xref:01-overview.adoc[Overview]
. xref:02-details.adoc[Technical Details]
. xref:03-module-01-value-prop.adoc[Module 1: Value Proposition]
...
```

#### `01-overview.adoc` (Business Scenario)
```asciidoc
= Demo Overview

== Customer Scenario

Global Financial Corp processes 50 million transactions daily. Their current ML deployment
process takes 2-3 weeks per model, causing delays in fraud detection updates.

== Business Challenge

* Manual deployment causes configuration drift
* Regulatory compliance reviews delay releases
* Limited visibility into model performance

== Red Hat Solution

Red Hat OpenShift AI provides:

* Automated deployment pipelines (90% faster)
* Built-in compliance validation (SOC2, GDPR)
* Real-time monitoring and rollback capabilities

== Business Impact

* **90% faster** model deployment (weeks → hours)
* **25% improvement** in fraud detection accuracy
* **100% compliance** with regulatory requirements
* **$2M annual savings** in operational costs
```

#### `02-details.adoc` (Technical Requirements)
```asciidoc
= Technical Details

== Demo Environment

Your demonstration environment includes:

* Red Hat OpenShift {ocp_version}
* Red Hat OpenShift AI {rhoai_version}
* Pre-configured fraud detection model
* Web console: {web_console_url}

== Presenter Prerequisites

* Familiarity with OpenShift web console
* Basic understanding of ML model deployment
* 15-20 minutes presentation time

== Demo Duration

Total time: ~30 minutes (3 modules × 10-15 minutes each)
```

#### `03-module-01-*.adoc` (First Module)
```asciidoc
= Module 1: Demonstrating Rapid Model Deployment

== Know: The Business Context

Traditional ML deployment in financial services faces critical challenges:

* **Manual processes**: Data scientists spend 60% of time on deployment, not innovation
* **Compliance bottlenecks**: Legal review adds 1-2 weeks per release
* **Production risks**: Configuration drift causes 40% of model failures

**Industry data**: According to link:https://www.gartner.com/...[Gartner 2025 ML Report^],
85% of ML models never reach production due to deployment complexity.

== Show: What You'll Demonstrate

In this module, you will demonstrate:

. Deploying a fraud detection model in under 5 minutes
. Automated compliance validation checks
. Real-time monitoring dashboard

=== Demonstration Steps

. Log into OpenShift AI dashboard at {web_console_url}
+
[.presenter-note]
****
**Presenter note**: Emphasize the unified interface - no context switching between tools.
**Timing**: 1 minute
****

. Navigate to Model Serving → Deploy New Model
+
[.presenter-note]
****
**Talking point**: "Notice how we can deploy directly from S3, Git, or internal registry.
This flexibility is unique to Red Hat - AWS SageMaker locks you into S3."
**Timing**: 2 minutes
****

. Select pre-configured fraud detection model
+
Show the automated validation checks:
- Schema compatibility ✓
- Compliance requirements (SOC2) ✓
- Resource limits validated ✓
+
[.presenter-note]
****
**Audience engagement**: Ask "How long does compliance review take in your organization?"
Highlight that Red Hat automates this completely.
**Timing**: 3 minutes
****

. Click Deploy and monitor progress
+
Show real-time logs and metrics as model initializes.
+
[.presenter-note]
****
**Competitive advantage**: "Unlike Azure ML, we provide full Kubernetes visibility.
You're not locked into a black box."
**Timing**: 4 minutes
****

=== Key Messages

After this demonstration, viewers should understand:

✅ Red Hat OpenShift AI **eliminates manual deployment** steps
✅ **Built-in compliance automation** de-risks production releases
✅ **Hybrid cloud flexibility** prevents vendor lock-in (vs AWS, Azure)
✅ **Enterprise support** ensures production readiness

=== Optional: Troubleshooting

If model deployment fails:

* Check service account permissions: `oc get sa -n {namespace}`
* Verify storage class: `oc get pvc`
* Review model logs: Click "View Logs" in dashboard

[.presenter-note]
****
**If questions arise**: Be prepared to explain:
- Why Kubernetes matters for ML (portability, scaling)
- How Red Hat differs from hyperscaler ML platforms
- Support model (24x7 enterprise support included)
****

== Competitive Positioning

| Feature | Red Hat OpenShift AI | AWS SageMaker | Azure ML |
|---------|---------------------|---------------|----------|
| **Hybrid Cloud** | ✅ On-prem + cloud | ❌ AWS only | ❌ Azure only |
| **Kubernetes Native** | ✅ Yes | ❌ Proprietary | ❌ Limited |
| **Compliance Automation** | ✅ Built-in | 🟡 Manual config | 🟡 Manual config |
| **Vendor Lock-in** | ❌ None | ✅ High | ✅ High |
| **Enterprise Support** | ✅ 24x7 included | 🟡 Paid add-on | 🟡 Paid add-on |
```

---

## Key Features

### 1. Know/Show Methodology

{: .tip }
> Every demo module has two sections: **Know** (business context) and **Show** (technical demonstration). This ensures presenters lead with value, not features.

**Know section includes:**
- Customer pain points (backed by industry data)
- Business impact of the problem
- Why traditional approaches fail
- References to analyst reports or customer stories

**Show section includes:**
- Step-by-step demonstration instructions
- Presenter notes with talking points
- Timing cues for each step
- Audience engagement prompts
- Competitive differentiators

---

### 2. Sequential Questioning

The skill asks **one question (or related group) at a time** and **waits for your answer**. This prevents overwhelming you with 20 questions at once.

**Example interaction:**
```
Skill: "What is the customer scenario for this demo?"
You: "Global bank struggles with slow ML deployment - takes 2-3 weeks
      per model, causing fraud detection delays"

Skill: "What quantified business impact can customers expect?"
You: "90% faster deployment, 25% better accuracy, $2M annual savings"

Skill: "What competitive advantages does Red Hat have?"
You: "Hybrid cloud (vs AWS lock-in), Kubernetes native (vs proprietary),
      compliance automation (vs manual processes)"
```

---

### 3. Business Impact Focus

Unlike workshops, demos emphasize **ROI and business metrics**:

✅ Quantified improvements (percentages, dollars, time savings)
✅ Competitive advantages (why Red Hat vs alternatives)
✅ Customer success stories (proof points)
✅ Risk mitigation (compliance, support, vendor lock-in)

**Example metrics:**
- "Reduce deployment time by **90%** (weeks → hours)"
- "Save **$2M annually** in operational costs"
- "Improve fraud detection accuracy by **25%**"
- "Achieve **100% compliance** with SOC2/GDPR"

---

### 4. Presenter Guidance

Every module includes detailed presenter notes:

**Timing cues:**
```
[.presenter-note]
****
**Timing**: 3 minutes for this section
****
```

**Talking points:**
```
[.presenter-note]
****
**Talking point**: "Notice how we can deploy from any source.
This flexibility prevents vendor lock-in, unlike AWS SageMaker."
****
```

**Audience engagement:**
```
[.presenter-note]
****
**Audience engagement**: Ask "How long does compliance review take
in your organization?" Highlight automation benefits.
****
```

---

### 5. Competitive Positioning

Demos include comparison tables showing Red Hat advantages:

```asciidoc
| Feature | Red Hat | AWS | Azure | Google Cloud |
|---------|---------|-----|-------|--------------|
| Hybrid Cloud | ✅ | ❌ | ❌ | ❌ |
| Open Source | ✅ | ❌ | ❌ | ❌ |
| No Lock-in | ✅ | ❌ | ❌ | ❌ |
```

---

## Best Practices

### 1. Lead with Business Value, Not Features

❌ **Don't start with features:**
```asciidoc
Red Hat OpenShift AI has automated deployment pipelines,
compliance validation, and monitoring dashboards.
```

✅ **Start with business impact:**
```asciidoc
Global Financial Corp reduced model deployment time from 3 weeks to 4 hours,
saving $2M annually while ensuring SOC2 compliance.

How? Red Hat OpenShift AI automates deployment, compliance, and monitoring.
```

**Why:** Decision makers care about outcomes, not features.

---

### 2. Quantify Everything

❌ **Vague claims:**
```asciidoc
Red Hat OpenShift AI is faster and more efficient.
```

✅ **Quantified metrics:**
```asciidoc
According to link:https://www.forrester.com/...[Forrester TEI Study^],
Red Hat OpenShift AI customers achieve:

* 90% reduction in deployment time
* 25% improvement in model accuracy
* $2.1M NPV over 3 years
* 6-month payback period
```

**Why:** Numbers build credibility and justify investment.

---

### 3. Include Competitive Differentiators

Every module should answer: "Why Red Hat over AWS/Azure/Google?"

```asciidoc
== Why Red Hat OpenShift AI?

✅ **Hybrid cloud**: Deploy on-premises, edge, or any cloud (AWS locks you into AWS)
✅ **Open source**: No vendor lock-in, full Kubernetes compatibility
✅ **Enterprise support**: 24x7 support included (AWS charges extra)
✅ **Compliance built-in**: Automated SOC2/GDPR validation (Azure requires manual config)
```

**Why:** Presenters need ammunition to handle objections.

---

### 4. Prepare for Q&A

Include common objections and responses:

```asciidoc
== Anticipated Questions

**Q: "What about cost compared to AWS SageMaker?"**
A: While AWS appears cheaper initially, hidden costs (egress fees, support,
lock-in migration costs) make Red Hat 30% more cost-effective over 3 years.
See link:https://...[Forrester TEI Study^] for details.

**Q: "Can we migrate existing Azure ML workloads?"**
A: Yes. Red Hat OpenShift AI supports standard ONNX and TensorFlow formats.
Migration typically takes 2-4 weeks with Red Hat Consulting support.

**Q: "What about edge deployments?"**
A: Red Hat supports Single Node OpenShift (SNO) for edge locations.
AWS SageMaker requires full AWS infrastructure.
```

---

### 5. Keep Modules Short (10-15 min)

❌ **Too long (30 min module):**
- Covers 5 different capabilities
- Loses audience attention
- Hard to recover from technical issues

✅ **Right size (10-15 min module):**
- 1-2 related capabilities
- Clear beginning and end
- Easy to skip or extend based on audience

**Why:** Shorter modules maintain engagement and provide flexibility.

---

## Example Session

Here's a typical create-demo workflow:

```bash
$ cd ~/showroom-openshift-ai-demo
$ claude

Claude Code> /create-demo --new

Welcome to Demo Module Creator!

I'll guide you through creating a new presenter-led demonstration.

Step 1: Determine Demo Status
This is a NEW demo (creating from scratch).

Step 2: Plan Overall Demo Story

Q: What is the title of this demo?
A: Accelerating AI Model Deployment with Red Hat OpenShift AI

Q: What customer scenario will you use?
A: Global Financial Corp processes 50M transactions daily. Their ML deployment
   takes 2-3 weeks per model, delaying fraud detection updates and costing $5M
   annually in manual effort.

Q: What quantified business impact can customers expect?
A: - 90% faster deployment (weeks → hours)
   - 25% improvement in fraud detection accuracy
   - $2M annual savings in operational costs
   - 100% compliance with SOC2/GDPR

Q: How will the presentation unfold across modules?
A: Module 1: Business challenge and value proposition
   Module 2: Technical demonstration of rapid deployment
   Module 3: Results, ROI, and call-to-action

Q: Who is the target audience (decision makers)?
A: VP of Technology, Chief Data Officer, ML Engineering leads

Excellent! Demo story established.

Step 3: Gather Module-Specific Details

Q: What is the title of this module?
A: Demonstrating Rapid Model Deployment

Q: What business context must viewers understand (Know section)?
A: - Traditional ML deployment takes 2-3 weeks (60% of data scientist time)
   - Compliance reviews add 1-2 weeks delay
   - Configuration drift causes 40% of production failures
   - Industry stat: 85% of ML models never reach production (Gartner)

Q: What will you demonstrate (Show section)?
A: 1. Deploy fraud detection model in under 5 minutes
   2. Show automated compliance validation (SOC2)
   3. Display real-time monitoring dashboard
   4. Demonstrate one-click rollback capability

Q: What 3-5 key messages should viewers remember?
A: 1. Red Hat eliminates manual deployment steps (automation)
   2. Built-in compliance de-risks production (governance)
   3. Hybrid cloud prevents vendor lock-in (flexibility)
   4. Enterprise support ensures production readiness (confidence)

Q: Estimated presentation time for this module?
A: 10-15 minutes

Q: What competitive advantages vs AWS/Azure/Google?
A: - Hybrid cloud (AWS locks to AWS, Azure locks to Azure)
   - Kubernetes native (not proprietary platforms)
   - Compliance built-in (vs manual config)
   - No vendor lock-in (open source standards)
   - Enterprise support included (vs paid add-ons)

[Steps 4-7 continue with variables, diagrams, presenter notes...]

Step 8: Generating Files

Creating demo files:
  ✓ 00-index.adoc
  ✓ 01-overview.adoc
  ✓ 02-details.adoc
  ✓ 03-module-01-rapid-deployment.adoc

Step 10: Updating Navigation
  ✓ nav.adoc updated

Demo module created successfully!

Next steps:
1. Review generated files in content/modules/ROOT/pages/
2. Add screenshots/diagrams to assets/images/
3. Practice the demonstration to validate timing
4. Run /verify-content to check quality
5. When ready for Module 2, run /create-demo --continue
```

---

## Troubleshooting

### Skill Doesn't Detect Existing Modules

**Problem:** Running `/create-demo --continue` but skill thinks it's new

**Cause:** Missing or incorrectly named files

**Solution:**
1. Check file naming: Must be `0X-module-YY-*.adoc` pattern
2. Ensure files are in `content/modules/ROOT/pages/`
3. Restart Claude Code session

---

### Business Impact Metrics Unclear

**Problem:** Unsure what quantified metrics to include

**Cause:** Lack of customer data or industry research

**Solution:**
- Use link:https://www.forrester.com[Forrester^] Total Economic Impact studies
- Reference link:https://www.gartner.com[Gartner^] industry reports
- Cite Red Hat customer success stories from link:https://www.redhat.com/en/success-stories[Red Hat website^]
- Use conservative estimates if customer data unavailable
- Include disclaimer: "Based on industry benchmarks" or "Typical customer results"

---

### Competitive Positioning Unknown

**Problem:** Don't know how Red Hat compares to AWS/Azure

**Cause:** Unfamiliar with competitor offerings

**Solution:**
- Review Red Hat competitive battle cards (internal Sales resources)
- Consult Product Marketing team for latest positioning
- Use link:https://www.redhat.com/en/resources/openshift-vs-aws-overview[Red Hat comparison guides^]
- Focus on proven differentiators: hybrid cloud, open source, no lock-in

---

## Related Resources

- [Verify Content](verify-content) - Validate created demos
- [Create Lab](create-lab) - Create workshops instead
- [Setup Guide](../setup) - Install create-demo skill
- [Quick Reference](../reference) - Command cheatsheet
- [Red Hat Style Guide](https://redhat-documentation.github.io/supplementary-style-guide/) - Writing standards
