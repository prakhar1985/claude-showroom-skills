---
layout: default
title: Quick Reference
nav_order: 6
description: "Quick reference guide for Showroom Skills commands and patterns"
---

# Quick Reference
{: .no_toc }

Cheatsheet for common commands, patterns, and standards.
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Installation

### One-Time Setup

```bash
# Clone nookbag template
git clone https://github.com/rhpds/showroom-template-nookbag.git
cd showroom-template-nookbag

# Copy to home directory
cp -r .claude ~/.claude

# Start Claude Code
claude

# Verify installation
/help
```

---

## Available Skills

| Command | Purpose | Use Case |
|---------|---------|----------|
| `/verify-content` | Validate content quality | Before publishing, after reviews |
| `/create-lab` | Create workshop module | Hands-on learning content |
| `/create-demo` | Create demo module | Presenter-led demonstrations |
| `/blog-generate` | Transform to blog post | Marketing content, developer blogs |

---

## Common Workflows

### Creating a New Workshop

```bash
# Navigate to project
cd ~/showroom-my-workshop

# Start Claude Code
claude

# Create first module
/create-lab --new

# Answer questions sequentially
# (workshop title, scenario, objectives, etc.)

# Create additional modules
/create-lab --continue
/create-lab --continue

# Validate content
/verify-content

# Fix issues and re-validate
/verify-content
```

---

### Creating a New Demo

```bash
# Navigate to project
cd ~/showroom-my-demo

# Start Claude Code
claude

# Create first module
/create-demo --new

# Answer questions sequentially
# (business scenario, ROI, competitive advantages, etc.)

# Create additional modules
/create-demo --continue
/create-demo --continue

# Validate content
/verify-content
```

---

### Validating Existing Content

```bash
# Navigate to project with existing content
cd ~/showroom-existing-project

# Start Claude Code
claude

# Run verification
/verify-content

# Review detailed sections in output
# (Scroll to bottom for summary table)

# Fix issues and re-run
/verify-content
```

---

## File Locations

### Global Skills Directory

```
~/.claude/
├── skills/                    # Skill definitions
│   ├── create-lab/
│   │   └── SKILL.md
│   ├── create-demo/
│   │   └── SKILL.md
│   ├── verify-content/
│   │   └── SKILL.md
│   └── blog-generate/
│       └── SKILL.md
│
├── prompts/                   # Verification prompts (11 files)
│   ├── enhanced_verification_workshop.txt
│   ├── enhanced_verification_demo.txt
│   ├── redhat_style_guide_validation.txt
│   └── ... (8 more files)
│
└── docs/                      # Shared rules
    └── SKILL-COMMON-RULES.md
```

### Project Content Directory

```
content/modules/ROOT/
├── pages/
│   ├── 00-index.adoc         # Landing page
│   ├── 01-overview.adoc      # Scenario + objectives
│   ├── 02-details.adoc       # Technical requirements
│   ├── 03-module-01-*.adoc   # First module
│   ├── 04-module-02-*.adoc   # Second module
│   └── 0X-conclusion.adoc    # Conclusion (mandatory)
│
├── partials/
│   └── _attributes.adoc      # Version variables
│
└── nav.adoc                  # Navigation menu
```

---

## Common Validation Fixes

### External Links (Missing Caret)

**Problem:**
```asciidoc
link:https://docs.redhat.com[Red Hat Documentation]
```

**Fix:**
```asciidoc
link:https://docs.redhat.com[Red Hat Documentation^]
                                                   ↑ Add caret
```

---

### Lists (Missing Blank Lines)

**Problem:**
```asciidoc
**Prerequisites:**
* OpenShift 4.18
* Admin access
Next section...
```

**Fix:**
```asciidoc
**Prerequisites:**

* OpenShift 4.18
* Admin access

Next section...
```

---

### Images (Not Clickable)

**Problem:**
```asciidoc
image::diagram.png[System architecture,width=600]
```

**Fix:**
```asciidoc
image::diagram.png[System architecture,link=self,window=blank,width=600]
```

---

### Em Dashes

**Problem:**
```asciidoc
OpenShift—Red Hat's platform—simplifies deployments.
```

**Fix:**
```asciidoc
OpenShift, Red Hat's platform, simplifies deployments.
```

---

### Product Name Abbreviations

**Problem:**
```asciidoc
Deploy to OCP using the CLI.
```

**Fix:**
```asciidoc
Deploy to Red Hat OpenShift using the command line.
```

---

## Red Hat Style Essentials

### Product Names

Always use full product names (especially on first use and in headings):

| ❌ Abbreviation | ✅ Full Name |
|----------------|-------------|
| OCP | Red Hat OpenShift |
| RHEL | Red Hat Enterprise Linux |
| ODF | Red Hat OpenShift Data Foundation |
| ACM | Red Hat Advanced Cluster Management |
| ACS | Red Hat Advanced Cluster Security |
| AAP | Red Hat Ansible Automation Platform |
| RHOAI | Red Hat OpenShift AI |

---

### Version Attributes

❌ **Don't hardcode versions:**
```asciidoc
Install OpenShift 4.18 using...
```

✅ **Use attributes:**
```asciidoc
Install Red Hat OpenShift {ocp_version} using...
```

**Define in `partials/_attributes.adoc`:**
```asciidoc
:ocp_version: 4.18
:rhel_version: 9.5
:ansible_version: 2.17
```

---

### Numbers

✅ **Use numerals (not spelled out):**
```asciidoc
5 steps
3 modules
10 minutes
```

❌ **Don't spell out:**
```asciidoc
five steps
three modules
ten minutes
```

---

### Heading Case

✅ **Use sentence case:**
```asciidoc
== Deploying your first application
== What you will learn
```

❌ **Don't use title case:**
```asciidoc
== Deploying Your First Application
== What You Will Learn
```

---

### Inclusive Language

| ❌ Avoid | ✅ Use Instead |
|---------|---------------|
| whitelist | allowlist |
| blacklist | blocklist |
| master/slave | primary/secondary, leader/follower |
| sanity check | confidence check, verification |
| guys | folks, team, everyone |

---

## AsciiDoc Formatting

### List Markers

**Bullets (`*`) for knowledge/information:**
```asciidoc
**Key concepts:**

* Projects organize resources
* Pods are the smallest deployable units
* Services provide stable networking
```

**Numbers (`.`) for sequential steps:**
```asciidoc
**Exercise:**

. Log into OpenShift web console
. Create new project named `my-app`
. Deploy application from Git
```

---

### Code Blocks

**Always specify language:**
```asciidoc
[source,bash]
----
oc get pods -n my-app
----

[source,yaml]
----
apiVersion: v1
kind: Service
metadata:
  name: my-service
----
```

---

### External Links

**Always open in new tab (`^`):**
```asciidoc
See link:https://docs.redhat.com[Red Hat Documentation^] for details.
                                                        ↑
```

---

### Internal References

**Use xref for cross-references:**
```asciidoc
See xref:03-module-01-setup.adoc[Module 1: Setup] for details.
```

---

### Admonitions

```asciidoc
NOTE: This is informational.

TIP: This is a helpful suggestion.

IMPORTANT: This is critical information.

WARNING: This could cause issues.

CAUTION: This could cause data loss.
```

---

## Workshop Structure Requirements

### Mandatory Elements

Every workshop **must** include:

1. **Learning objectives** in each module
   ```asciidoc
   == Learning Objectives

   After completing this module, you will be able to:

   * Deploy applications to Red Hat OpenShift
   * Configure application settings
   * Troubleshoot common issues
   ```

2. **Verification steps** for hands-on exercises
   ```asciidoc
   === Verify

   Confirm deployment succeeded:

   [source,bash]
   ----
   oc get pods -n my-app
   ----

   Expected: Pod shows STATUS: Running
   ```

3. **Conclusion module** with consolidated references
   ```asciidoc
   = Conclusion

   == Summary

   In this workshop, you learned:

   * Key skill 1
   * Key skill 2
   * Key skill 3

   == References

   * link:https://...[Red Hat Documentation^]
   * link:https://...[Product Guide^]
   ```

---

## Demo Structure Requirements

### Know/Show Sections

Every demo module has two parts:

**Know (Business Context):**
```asciidoc
== Know: The Business Context

* Customer pain point 1
* Customer pain point 2
* Industry challenges

**Industry data**: According to link:...[Gartner 2025 Report^],
85% of enterprises face this challenge.
```

**Show (Technical Demonstration):**
```asciidoc
== Show: What You'll Demonstrate

. Step 1 with presenter notes
+
[.presenter-note]
****
**Talking point**: Emphasize the business value here.
**Timing**: 2 minutes
****

. Step 2 with competitive advantage
+
[.presenter-note]
****
**Competitive advantage**: Unlike AWS, Red Hat supports hybrid cloud.
****
```

---

## Accessibility Requirements (WCAG 2.1 AA)

### Image Alt Text

**Always provide descriptive alt text:**
```asciidoc
image::architecture-diagram.png[System architecture showing three-tier application with load balancer, application servers, and database,link=self,window=blank,width=800]
```

---

### Link Descriptions

❌ **Don't use "click here":**
```asciidoc
For more info, link:url[click here].
```

✅ **Use descriptive text:**
```asciidoc
See link:url[Red Hat OpenShift documentation^] for installation instructions.
```

---

### Heading Hierarchy

✅ **Logical order:**
```asciidoc
= Module Title (H1)
== Main Section (H2)
=== Subsection (H3)
==== Detail (H4)
```

❌ **Don't skip levels:**
```asciidoc
= Module Title (H1)
=== Subsection (H3)  ← Skipped H2
```

---

## Command Quick Reference

### Verification

```bash
/verify-content              # Validate all content
```

### Workshop Creation

```bash
/create-lab --new            # Start new workshop
/create-lab --continue       # Add module to existing workshop
```

### Demo Creation

```bash
/create-demo --new           # Start new demo
/create-demo --continue      # Add module to existing demo
```

### Blog Generation

```bash
/blog-generate               # Transform workshop/demo to blog post
```

---

## Troubleshooting Quick Fixes

### Skills not appearing

```bash
# Re-copy skills
cp -r /path/to/showroom-template-nookbag/.claude ~/.claude

# Restart Claude Code
exit
claude
```

---

### Verification fails (prompts not found)

```bash
# Copy prompts
cp -r /path/to/showroom-template-nookbag/.claude/prompts ~/.claude/

# Verify all 11 files present
ls ~/.claude/prompts/ | wc -l
# Should output: 11
```

---

### create-lab doesn't detect existing modules

```bash
# Check file naming (must match pattern)
ls content/modules/ROOT/pages/

# Expected: 03-module-01-*.adoc, 04-module-02-*.adoc
# Fix: Rename files to match pattern
```

---

## Update Skills

```bash
# Navigate to nookbag template
cd /path/to/showroom-template-nookbag

# Pull latest changes
git pull origin main

# Re-copy to home directory
cp -r .claude ~/.claude

# Restart Claude Code
exit
claude
```

---

## Related Resources

### Documentation
- [Setup Guide](setup) - Detailed installation instructions
- [Verify Content](skills/verify-content) - Validation skill details
- [Create Lab](skills/create-lab) - Workshop creation workflow
- [Create Demo](skills/create-demo) - Demo creation workflow
- [Troubleshooting](troubleshooting) - Common issues and solutions

### External Resources
- [Official Claude Code Docs](https://code.claude.com/docs)
- [Anthropic Skills Repository](https://github.com/anthropics/skills)
- [Nookbag Template](https://github.com/rhpds/showroom-template-nookbag)
- [Red Hat Style Guide](https://redhat-documentation.github.io/supplementary-style-guide/)
- [AsciiDoc Syntax Reference](https://docs.asciidoctor.org/asciidoc/latest/syntax-quick-reference/)
- [Showroom Platform Docs](https://redhat-scholars.github.io/showroom-docs/)

---

## Getting Help

### GitHub Issues
- [claude-showroom-skills Issues](https://github.com/psrivast/claude-showroom-skills/issues)
- [showroom-template-nookbag Issues](https://github.com/rhpds/showroom-template-nookbag/issues)

### Red Hat Internal
- **Slack**: #demo-platform channel
- **Email**: rhdp-support@redhat.com

---

{: .note }
> **Tip**: Bookmark this page for quick access to common commands and patterns!
