---
layout: default
title: Setup & Installation
nav_order: 2
description: "How to install and configure Red Hat Showroom Skills for Claude Code"
---

# Setup & Installation
{: .no_toc }

Complete guide to installing and configuring Showroom Skills for Claude Code.
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Prerequisites

Before installing Showroom Skills, ensure you have:

- ✅ **Claude Code CLI** or **Cursor IDE** installed and configured
- ✅ **Git** command line tools
- ✅ **Terminal** access (macOS Terminal, Linux shell, or Windows WSL)
- ✅ **Basic command line** familiarity

{: .note }
> **New to Claude Code?** Install it from [code.claude.com](https://code.claude.com) or use Cursor IDE as an alternative.

---

## Installation Steps

### Step 1: Clone the Nookbag Template

The nookbag template repository contains all the skills, prompts, and templates you need.

```bash
git clone https://github.com/rhpds/showroom-template-nookbag.git
cd showroom-template-nookbag
```

**What this gives you:**
- 4 core skills (`create-lab`, `create-demo`, `verify-content`, `blog-generate`)
- 11 verification prompt files
- Shared rules and documentation
- Workshop and demo templates
- Validation hooks

---

### Step 2: Copy Skills to Your Home Directory

Skills need to be in your home directory (`~/.claude/`) to work globally across all projects.

#### Option A: Copy Everything (Recommended)

```bash
# Copy the entire .claude directory to your home
cp -r .claude ~/.claude
```

This copies:
- `~/.claude/skills/` - All 4 skills
- `~/.claude/prompts/` - All 11 verification prompts
- `~/.claude/docs/` - Shared rules (SKILL-COMMON-RULES.md)
- `~/.claude/hooks/` - Validation hooks
- `~/.claude/agents/` - AI validation agents
- `~/.claude/templates/` - Reference templates

#### Option B: Copy Individual Components

If you already have a `.claude/` directory, copy selectively:

```bash
# Copy skills
cp -r .claude/skills ~/.claude/

# Copy prompts (required for verify-content)
cp -r .claude/prompts ~/.claude/

# Copy shared documentation
cp -r .claude/docs ~/.claude/
```

{: .warning }
> **Important:** The `verify-content` skill requires all files in `.claude/prompts/` to function correctly. Don't skip copying prompts!

---

### Step 3: Verify Installation

Test that skills are properly installed and discovered by Claude Code.

```bash
# Navigate to any directory
cd ~

# Start Claude Code
claude

# In the Claude Code session, type:
/help
```

**Expected output:**

You should see the Showroom skills listed:

```
Available custom skills:
  /verify-content    Validate workshop/demo content quality
  /create-lab        Create workshop module with guided workflow
  /create-demo       Create demo module with Know/Show structure
  /blog-generate     Transform content to blog posts
```

{: .tip }
> If skills don't appear, check the [Troubleshooting](troubleshooting) page for common issues.

---

## Directory Structure Explained

After installation, your `~/.claude/` directory structure looks like this:

```
~/.claude/
├── skills/                         # Skill definitions
│   ├── create-lab/
│   │   └── SKILL.md               # Workshop creation skill
│   ├── create-demo/
│   │   └── SKILL.md               # Demo creation skill
│   ├── verify-content/
│   │   └── SKILL.md               # Content validation skill
│   └── blog-generate/
│       └── SKILL.md               # Blog transformation skill
│
├── prompts/                        # Verification frameworks
│   ├── enhanced_verification_workshop.txt
│   ├── enhanced_verification_demo.txt
│   ├── redhat_style_guide_validation.txt
│   ├── verify_accessibility_compliance_workshop.txt
│   ├── verify_accessibility_compliance_demo.txt
│   ├── verify_technical_accuracy_workshop.txt
│   ├── verify_technical_accuracy_demo.txt
│   ├── verify_workshop_structure.txt
│   └── verify_content_quality.txt
│
├── docs/
│   └── SKILL-COMMON-RULES.md      # Shared contracts between skills
│
├── hooks/
│   └── validate-paths.sh          # Pre-execution path validation
│
├── agents/                         # AI validation agents
│   ├── workshop-reviewer.md
│   ├── style-enforcer.md
│   ├── technical-editor.md
│   └── ... (8 total agents)
│
└── templates/                      # Reference examples
    ├── workshop/
    └── demo/
```

### What Each Directory Does

| Directory | Purpose |
|-----------|---------|
| `skills/` | Core skill definitions (SKILL.md files) |
| `prompts/` | Validation prompts used by verify-content skill |
| `docs/` | Shared rules and standards (SKILL-COMMON-RULES.md) |
| `hooks/` | Pre-execution validation scripts |
| `agents/` | AI agent specifications for content review |
| `templates/` | Reference examples for workshops and demos |

---

## Optional: Configure for Cursor IDE

If you use Cursor IDE instead of Claude Code CLI:

1. **Open your Showroom project in Cursor**
2. **Skills auto-load** from the project's `.claude/skills/` directory
3. **Use slash commands** in Cursor's chat: `/verify-content`, `/create-lab`, `/create-demo`

{: .note }
> Cursor reads skills from both `~/.claude/skills/` (global) and `.claude/skills/` (project-specific). For Showroom projects, keep skills in `~/.claude/` for global access.

Detailed Cursor setup: See `CURSOR-SKILLS-README.adoc` in the nookbag template.

---

## Updating Skills

To update skills when the nookbag template is updated:

```bash
# Navigate to nookbag template
cd path/to/showroom-template-nookbag

# Pull latest changes
git pull origin main

# Re-copy to home directory
cp -r .claude ~/.claude

# Restart Claude Code session
```

{: .warning }
> Copying will overwrite your existing `~/.claude/` files. Back up any custom modifications first.

---

## Next Steps

Now that skills are installed:

1. **Try verify-content**: [Validate existing content](skills/verify-content)
2. **Create your first lab**: [Workshop creation guide](skills/create-lab)
3. **Create a demo**: [Demo creation guide](skills/create-demo)
4. **Bookmark quick reference**: [Command cheatsheet](reference)

---

## Troubleshooting

If you encounter issues:

- **Skills not appearing?** See [Skills not appearing](troubleshooting#skills-not-appearing)
- **Verification errors?** See [Verification errors](troubleshooting#verification-errors)
- **File generation issues?** See [File generation issues](troubleshooting#file-generation-issues)

Full troubleshooting guide: [Troubleshooting & FAQ](troubleshooting)

---

## System Requirements Details

### Supported Operating Systems

- ✅ macOS (Intel and Apple Silicon)
- ✅ Linux (Ubuntu, Fedora, RHEL, Debian)
- ✅ Windows (via WSL2)

### Claude Code Versions

- Minimum: Claude Code v1.0+
- Recommended: Latest version from [code.claude.com](https://code.claude.com)

### Disk Space

- Skills: ~5 MB
- Prompts and docs: ~2 MB
- Total: ~7 MB

### Network Requirements

- Internet connection for Claude API calls
- No additional network configuration needed
