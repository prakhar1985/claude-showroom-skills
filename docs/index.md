---
layout: default
title: Home
nav_order: 1
description: "Claude Code skills for creating high-quality Red Hat workshop and demo content"
permalink: /
---

# Red Hat Showroom Skills for Claude Code
{: .fs-9 }

Professional content creation skills for building high-quality Red Hat workshops and demos.
{: .fs-6 .fw-300 }

[Get Started](setup){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[View on GitHub](https://github.com/rhpds/showroom-template-nookbag){: .btn .fs-5 .mb-4 .mb-md-0 }

---

## What are Showroom Skills?

Showroom Skills are Claude Code plugins that guide you through creating workshop and demo content that meets Red Hat quality standards. They automate content structure, enforce style guidelines, and ensure accessibility compliance.

### Why use these skills?

✅ **Quality Assurance**: Automatic validation against Red Hat Style Guide and WCAG 2.1 AA standards
✅ **Consistency**: Standardized structure across all workshop and demo content
✅ **Time Savings**: Guided workflows reduce content creation time by 60%
✅ **Best Practices**: Built-in Red Hat expertise and proven patterns
✅ **Accessibility**: Ensure all content meets accessibility requirements

---

## Quick Start

Get up and running in 3 simple steps:

### 1. Clone the Template

```bash
git clone https://github.com/rhpds/showroom-template-nookbag.git
cd showroom-template-nookbag
```

### 2. Copy Skills to Your Home Directory

```bash
cp -r .claude ~/.claude
```

### 3. Start Using Skills

```bash
# Start Claude Code
claude

# Use the skills
/verify-content    # Validate content quality
/create-lab        # Create workshop module
/create-demo       # Create demo module
```

[Detailed Setup Instructions](setup){: .btn .btn-blue }

---

## Available Skills

<div class="code-example" markdown="1">

### `/verify-content`
{: .text-purple-000}

Validate workshop and demo content against Red Hat standards.

**Checks:**
- Red Hat Style Guide compliance
- AsciiDoc formatting
- Accessibility (WCAG 2.1 AA)
- Technical accuracy
- Workshop structure

[Learn More →](skills/verify-content)

---

### `/create-lab`
{: .text-purple-000}

Create workshop modules with guided step-by-step workflow.

**Features:**
- Sequential questioning workflow
- Auto-generated file structure
- Verification checkpoints
- Story continuity across modules

[Learn More →](skills/create-lab)

---

### `/create-demo`
{: .text-purple-000}

Create presenter demos with Know/Show methodology.

**Features:**
- Business-focused messaging
- Presenter guidance
- ROI and metrics focus
- Q&A preparation

[Learn More →](skills/create-demo)

</div>

---

## System Requirements

- **Claude Code CLI** or **Cursor IDE** installed
- **Git** for cloning the template
- **Basic terminal/command line** knowledge
- **AsciiDoc** familiarity (helpful but not required)

---

## What Gets Created?

When you use these skills, you get professional content with:

✅ **Proper file structure** (`index.adoc`, `overview.adoc`, `details.adoc`, modules)
✅ **Red Hat branding** and terminology
✅ **Accessibility features** (alt text, proper headings, WCAG compliance)
✅ **Learning objectives** and verification steps
✅ **Mandatory conclusion** with consolidated references
✅ **Navigation** auto-maintained

---

## Documentation

<div class="code-example" markdown="1">

**Getting Started**
- [Setup & Installation](setup)
- [Quick Reference](reference)
- [Troubleshooting](troubleshooting)

**Skills**
- [Verify Content](skills/verify-content)
- [Create Lab](skills/create-lab)
- [Create Demo](skills/create-demo)

**Resources**
- [Official Claude Code Docs](https://code.claude.com/docs)
- [Anthropic Skills Repository](https://github.com/anthropics/skills)
- [Nookbag Template](https://github.com/rhpds/showroom-template-nookbag)
- [Red Hat Style Guide](https://redhat-documentation.github.io/supplementary-style-guide/)

</div>

---

## Credits

These skills were created and developed by:

- **Prakhar Srivastava** - Manager, Technical Marketing, Red Hat
- **Nate Stephany** - RHDP Catalog Owner, Red Hat

With mentorship from **Tony**.

---

## Need Help?

- **GitHub Issues**: [Report a problem](https://github.com/psrivast/claude-showroom-skills/issues)
- **Red Hat Internal**: #demo-platform Slack channel
- **Documentation**: Browse the guides on the left sidebar

---

{: .note }
> These skills are designed for Red Hat content creators. They enforce Red Hat Corporate Style Guide standards and Showroom platform requirements.
