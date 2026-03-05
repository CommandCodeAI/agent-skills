<h1 align="center">
    Awesome Skills
</h1>

<a href="https://commandcode.ai/skills" target="_blank">
    <img src="https://github.com/user-attachments/assets/4f7d30fa-9482-4db0-8f59-25fb75c6edbd">
</a>

A curated list of practical Skills for enhancing workflows and capabilities of coding agents.

<br />

## Contents

- [What Are Skills?](#what-are-skills)
- [Skills](#skills)
  - [Software Development](#software-development)
  - [Cloud Infrastructure & AWS](#cloud-infrastructure--aws)
  - [Cloudflare](#cloudflare)
  - [Content & Communication](#content--communication)
  - [Visual Design & Media](#visual-design--media)
  - [Business Operations](#business-operations)
  - [Document Management](#document-management)
  - [Data Analytics](#data-analytics)
  - [Workflow Automation](#workflow-automation)
- [Getting Started](#getting-started)
- [Skill Structure](#skill-structure)
- [Contributing](#contributing)

## What Are Skills?

Skills are customizable workflows that teach AI assistants how to perform specific tasks according to your unique requirements. Skills enable AI assistants to execute tasks in a repeatable, standardized manner across different platforms and interfaces.

Skills work seamlessly with **Command Code**  providing consistent, high-quality outputs that follow best practices and maintain code quality standards.

## Skills

### Software Development

- **[artifacts-builder](skills/artifacts-builder/)** - Suite of tools for creating elaborate, multi-component HTML artifacts using modern frontend web technologies (React, Tailwind CSS, shadcn/ui).
- **[Brainstorming](skills/brainstorming/)** - Activates before writing code. Refines rough ideas through questions, explores alternatives, presents design in sections for validation, and saves design document.
- **[Changelog Generator](skills/changelog-generator/)** - Automatically creates user-facing changelogs from git commits by analyzing history and transforming technical commits into customer-friendly release notes.
- **[MCP Builder](skills/mcp-builder/)** - Guides creation of high-quality MCP (Model Context Protocol) servers for integrating external APIs and services with LLMs using Python or TypeScript.
- **[Playwright](skills/playwright-skill/)** - Complete browser automation with Playwright. Auto-detects dev servers, writes clean test scripts, tests pages, fills forms, takes screenshots, checks responsive design, validates UX, tests login flows, and automates any browser task.
- **[Receiving Code Review](skills/receiving-code-review/)** - Handles code review feedback with technical rigor and verification. Requires understanding before implementing, asks clarifying questions, and evaluates suggestions against codebase reality.
- **[Requesting Code Review](skills/requesting-code-review/)** - Requests code review after completing tasks or major features. Dispatches subagent to catch issues before merging, ensuring work meets requirements.
- **[Skill Creator](skills/skill-creator/)** - Provides guidance for creating effective AI Skills that extend capabilities with specialized knowledge, workflows, and tool integrations.
- **[Using Git Worktrees](skills/using-git-worktrees/)** - Activates after design approval. Creates isolated workspace on new branch, runs project setup, and verifies clean test baseline for feature work.
- **[Webapp Testing](skills/webapp-testing/)** - Tests local web applications using Playwright for verifying frontend functionality, debugging UI behavior, and capturing screenshots.
- **[Writing Plans](skills/writing-plans/)** - Activates with approved design. Breaks work into bite-sized tasks (2-5 minutes each) with exact file paths, complete code, and verification steps.
- **[Writing Skills](skills/writing-skills/)** - Test-driven development for creating and editing skills. Write test cases, watch them fail, write the skill, watch tests pass, and refactor to close loopholes.

### Cloud Infrastructure & AWS

- **[AWS Agentic AI](skills/aws-agentic-ai/)** - Bedrock AgentCore skill for building AI agents with AWS Bedrock, including service-specific documentation and cross-service patterns.
- **[AWS CDK Development](skills/aws-cdk-development/)** - Infrastructure as code development using AWS CDK with patterns, references, and validation scripts for stack management.
- **[AWS Cost Operations](skills/aws-cost-operations/)** - Cost optimization and operations management with CloudWatch alarms, operations patterns, and cost monitoring strategies.
- **[AWS Serverless EDA](skills/aws-serverless-eda/)** - Serverless architecture and event-driven design patterns for building scalable, event-driven applications on AWS.

### Cloudflare

- **[Building MCP Server on Cloudflare](skills/building-mcp-server-on-cloudflare/)** - Build remote Model Context Protocol (MCP) servers on Cloudflare Workers with tools, OAuth authentication, and production deployment.
- **[Building AI Agent on Cloudflare](skills/building-ai-agent-on-cloudflare/)** - Build AI agents on Cloudflare using the Agents SDK with state management, real-time WebSockets, scheduled tasks, tool integration, and chat capabilities.

### Content & Communication

- **[Content Research Writer](skills/content-research-writer/)** - Assists in writing high-quality content by conducting research, adding citations, improving hooks, and providing section-by-section feedback.
- **[Internal Comms](skills/internal-comms/)** - Helps write internal communications including 3P updates, company newsletters, FAQs, status reports, and project updates using company-specific formats.
- **[Meeting Insights Analyzer](skills/meeting-insights-analyzer/)** - Analyzes meeting transcripts to uncover behavioral patterns including conflict avoidance, speaking ratios, filler words, and leadership style.
- **[NotebookLM](skills/notebooklm-skill/)** - Query Google NotebookLM notebooks directly for source-grounded, citation-backed answers from Gemini with browser automation, library management, and persistent authentication.

### Visual Design & Media

- **[Canvas Design](skills/canvas-design/)** - Creates beautiful visual art in PNG and PDF documents using design philosophy and aesthetic principles for posters, designs, and static pieces.
- **[Image Enhancer](skills/image-enhancer/)** - Improves image and screenshot quality by enhancing resolution, sharpness, and clarity for professional presentations and documentation.
- **[Slack GIF Creator](skills/slack-gif-creator/)** - Creates animated GIFs optimized for Slack with validators for size constraints and composable animation primitives.
- **[Theme Factory](skills/theme-factory/)** - Applies professional font and color themes to artifacts including slides, docs, reports, and HTML landing pages with 10 pre-set themes.
- **[Video Downloader](skills/video-downloader/)** - Downloads videos from YouTube and other platforms for offline viewing, editing, or archival with support for various formats and quality options.
- **[YouTube Transcript](skills/youtube-transcript/)** - Downloads transcripts and subtitles from YouTube videos using yt-dlp. Supports manual subtitles, auto-generated captions, and optional Whisper transcription fallback.

### Business Operations

- **[Brand Guidelines](skills/brand-guidelines/)** - Applies brand colors and typography to artifacts for consistent visual identity and professional design standards.
- **[Competitive Ads Extractor](skills/competitive-ads-extractor/)** - Extracts and analyzes competitors' ads from ad libraries to understand messaging and creative approaches that resonate.
- **[Domain Name Brainstormer](skills/domain-name-brainstormer/)** - Generates creative domain name ideas and checks availability across multiple TLDs including .com, .io, .dev, and .ai extensions.
- **[Lead Research Assistant](skills/lead-research-assistant/)** - Identifies and qualifies high-quality leads by analyzing your product, searching for target companies, and providing actionable outreach strategies.
- **[Product Manager Skills](https://github.com/Digidai/product-manager-skills)** - Senior PM agent with 6 knowledge domains, 12 templates, and 30+ frameworks covering discovery, strategy, delivery, SaaS metrics, PM career coaching (IC to CPO), and AI product craft.

### Document Management

- **[docx](skills/document-skills/docx/)** - Create, edit, analyze Word docs with tracked changes, comments, formatting.
- **[pdf](skills/document-skills/pdf/)** - Extract text, tables, metadata, merge & annotate PDFs.
- **[pptx](skills/document-skills/pptx/)** - Read, generate, and adjust slides, layouts, templates.
- **[xlsx](skills/document-skills/xlsx/)** - Spreadsheet manipulation: formulas, charts, data transformations.

### Data Analytics

- **[Developer Growth Analysis](skills/developer-growth-analysis/)** - Analyzes developer productivity and growth metrics.

### Workflow Automation

- **[File Organizer](skills/file-organizer/)** - Intelligently organizes files and folders by understanding context, finding duplicates, and suggesting better organizational structures.
- **[Invoice Organizer](skills/invoice-organizer/)** - Automatically organizes invoices and receipts for tax preparation by reading files, extracting information, and renaming consistently.
- **[Raffle Winner Picker](skills/raffle-winner-picker/)** - Randomly selects winners from lists, spreadsheets, or Google Sheets for giveaways and contests with cryptographically secure randomness.


## Getting Started

### Using Skills with Command Code

<p align="center">
<a href="https://commandcode.ai" target="_blank">
    <img src="https://commandcode.ai/docs/top.png" style="border:2px solid #bbb; border-radius:8px; box-shadow:0 2px 6px rgba(0,0,0,0.1);">
</a>
</p>

[Command Code](https://commandcode.ai) is a coding agent designed with taste and attention to detail. To use skills with Command Code:

1. Place the skill in your `.commandcode/skills` directory
2. Command Code will automatically detect and activate relevant skills based on your task
3. Skills enhance Command Code's capabilities with specialized knowledge and workflows


## Skill Structure

Each skill is a folder containing a `SKILL.md` file with YAML frontmatter:

```
skill-name/
├── SKILL.md          # Required: Skill instructions and metadata
├── scripts/          # Optional: Helper scripts
├── templates/        # Optional: Document templates
└── resources/        # Optional: Reference files
```

### Basic Skill Template

```markdown
---
name: my-skill-name
description: A clear description of what this skill does and when to use it.
---

# My Skill Name

Detailed description of the skill's purpose and capabilities.

## When to Use This Skill

- Use case 1
- Use case 2
- Use case 3

## Instructions

[Detailed instructions for the AI assistant on how to execute this skill]

## Examples

[Real-world examples showing the skill in action]
```


## Contributing

We welcome contributions! Please read our [Contributing Guidelines](CONTRIBUTING.md) for details on how to contribute to this project.


### Join the Community

- Follow us on [X](https://x.com/CommandCode_ai) for updates and news.
- Join our [Discord](https://langbase.com/discord) for support and discussion.
