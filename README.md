# Red Hat Showroom Skills for Claude Code

Claude Code skills for creating high-quality Red Hat workshop and demo content.

## Documentation

📚 **[View Full Documentation](https://psrivast.github.io/claude-showroom-skills)**

Complete guides for installation, usage, and troubleshooting.

---

## Quick Start

### 1. Clone the Nookbag Template

```bash
git clone https://github.com/rhpds/showroom_template_nookbag.git
cd showroom_template_nookbag
```

### 2. Copy Skills to Your Home Directory

```bash
cp -r .claude/. ~/.claude
```

### 3. Use the Skills

```bash
# Start Claude Code
claude

# Use the skills
/verify-content    # Validate content quality
/create-lab        # Create workshop module
/create-demo       # Create demo module
```

---

## Available Skills

| Skill | Purpose | Documentation |
|-------|---------|---------------|
| `/verify-content` | Validate workshop/demo content against Red Hat standards | [Docs](https://psrivast.github.io/claude-showroom-skills/skills/verify-content) |
| `/create-lab` | Create workshop modules with guided workflow | [Docs](https://psrivast.github.io/claude-showroom-skills/skills/create-lab) |
| `/create-demo` | Create presenter demos with Know/Show structure | [Docs](https://psrivast.github.io/claude-showroom-skills/skills/create-demo) |
| `/generate-agv-description` | Generate AgnosticV catalog description for RHDP | See nookbag template |
| `/blog-generate` | Transform workshop/demo content to blog posts | See nookbag template |

---

## What These Skills Do

### `/verify-content`
Validates your Showroom content against:
- Red Hat Corporate Style Guide
- AsciiDoc formatting standards
- WCAG 2.1 AA accessibility requirements
- Technical accuracy (version attributes, references)
- Workshop/demo structure requirements

### `/create-lab`
Guides you through creating workshops with:
- Sequential questioning workflow (one question at a time)
- Auto-generated file structure (index, overview, details, modules)
- Story continuity across modules
- Verification checkpoints in every module
- Mandatory conclusion with consolidated references

### `/create-demo`
Guides you through creating presenter demos with:
- Know/Show methodology (business context + technical demonstration)
- Business impact focus (ROI, metrics, competitive advantages)
- Presenter guidance (talk tracks, timing, Q&A preparation)
- Competitive positioning tables
- Optional troubleshooting (presenters handle issues live)

---

## Features

✅ **Quality Assurance**: Automatic validation against Red Hat standards
✅ **Consistency**: Standardized structure across all content
✅ **Time Savings**: Guided workflows reduce creation time by 60%
✅ **Best Practices**: Built-in Red Hat expertise and proven patterns
✅ **Accessibility**: Ensure all content meets WCAG 2.1 AA requirements

---

## Prerequisites

- **Claude Code CLI** or **Cursor IDE** installed
- **Git** for cloning the template repository
- **Basic terminal/command line** knowledge
- **AsciiDoc** familiarity (helpful but not required)

---

## Installation

Detailed installation instructions: [Setup Guide](https://psrivast.github.io/claude-showroom-skills/setup)

**Choose your tool:**
- **Claude Code CLI users**: Follow Quick Install below
- **Cursor IDE users**: See [Cursor Setup Guide](https://psrivast.github.io/claude-showroom-skills/setup#using-cursor-ide-without-claude-code-cli)

### Quick Install (Claude Code CLI)

```bash
# Clone nookbag template
git clone https://github.com/rhpds/showroom_template_nookbag.git
cd showroom_template_nookbag

# Copy skills and prompts to home directory
cp -r .claude/. ~/.claude

# Verify installation
claude
/help
# You should see: /verify-content, /create-lab, /create-demo
```

---

## Documentation

- 📖 [Setup & Installation](https://psrivast.github.io/claude-showroom-skills/setup)
- 📖 [Quick Reference](https://psrivast.github.io/claude-showroom-skills/reference)
- 📖 [Troubleshooting](https://psrivast.github.io/claude-showroom-skills/troubleshooting)
- 📖 [Verify Content Skill](https://psrivast.github.io/claude-showroom-skills/skills/verify-content)
- 📖 [Create Lab Skill](https://psrivast.github.io/claude-showroom-skills/skills/create-lab)
- 📖 [Create Demo Skill](https://psrivast.github.io/claude-showroom-skills/skills/create-demo)

---

## Common Use Cases

### Creating a New Workshop

```bash
cd ~/showroom-my-workshop
claude

# Create first module
/create-lab --new

# Create additional modules
/create-lab --continue

# Validate content
/verify-content
```

### Creating a New Demo

```bash
cd ~/showroom-my-demo
claude

# Create first module
/create-demo --new

# Create additional modules
/create-demo --continue

# Validate content
/verify-content
```

### Validating Existing Content

```bash
cd ~/showroom-existing-project
claude

# Run verification
/verify-content

# Fix issues and re-validate
/verify-content
```

---

## File Structure

After installation, your `~/.claude/` directory will contain:

```
~/.claude/
├── skills/                         # Skill definitions
│   ├── create-lab/
│   │   └── SKILL.md
│   ├── create-demo/
│   │   └── SKILL.md
│   ├── verify-content/
│   │   └── SKILL.md
│   └── blog-generate/
│       └── SKILL.md
│
├── prompts/                        # Verification prompts (11 files)
│   ├── enhanced_verification_workshop.txt
│   ├── enhanced_verification_demo.txt
│   ├── redhat_style_guide_validation.txt
│   └── ... (8 more files)
│
└── docs/                           # Shared rules
    └── SKILL-COMMON-RULES.md
```

---

## Troubleshooting

Common issues and solutions: [Troubleshooting Guide](https://psrivast.github.io/claude-showroom-skills/troubleshooting)

### Skills not appearing?

```bash
# Re-copy skills
cp -r /path/to/showroom_template_nookbag/.claude ~/.claude

# Restart Claude Code
exit
claude
```

### Verification fails?

```bash
# Ensure prompts are copied
ls ~/.claude/prompts/ | wc -l
# Should output: 11

# If missing, copy prompts
cp -r /path/to/showroom_template_nookbag/.claude/prompts ~/.claude/
```

---

## System Requirements

### Supported Operating Systems
- ✅ macOS (Intel and Apple Silicon)
- ✅ Linux (Ubuntu, Fedora, RHEL, Debian)
- ✅ Windows (via WSL2)

### Claude Code Versions
- Minimum: Claude Code v1.0+
- Recommended: Latest version from [code.claude.com](https://code.claude.com)

### Disk Space
- Skills and prompts: ~7 MB total

---

## Credits

These skills were created and developed by:

- **Prakhar Srivastava** - Manager, Technical Marketing, Red Hat
- **Nate Stephany** - Senior Principal Technical Marketing Manager, Red Hat

With mentorship from **Tony**.

---

## Related Resources

- [Nookbag Template](https://github.com/rhpds/showroom_template_nookbag) - Source repository with skills
- [Official Claude Code Docs](https://code.claude.com/docs) - Claude Code documentation
- [Anthropic Skills Repository](https://github.com/anthropics/skills) - Official skills examples
- [Red Hat Style Guide](https://redhat-documentation.github.io/supplementary-style-guide/) - Writing standards
- [AsciiDoc Syntax Reference](https://docs.asciidoctor.org/asciidoc/latest/syntax-quick-reference/) - AsciiDoc guide
- [Showroom Platform Docs](https://redhat-scholars.github.io/showroom-docs/) - Showroom platform

---

## Support

### GitHub Issues
- [Report a problem](https://github.com/psrivast/claude-showroom-skills/issues)
- [Request a feature](https://github.com/psrivast/claude-showroom-skills/issues/new)

### Red Hat Internal
- **Slack**: #demo-platform channel
- **Email**: rhdp-support@redhat.com

---

## License

MIT License - see LICENSE file for details.

---

## Contributing

Contributions welcome! Please:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

For major changes, please open an issue first to discuss proposed changes.

---

{: .note }
> These skills are designed for Red Hat content creators. They enforce Red Hat Corporate Style Guide standards and Showroom platform requirements.
