# Nano Banana Pro Prompts Recommend Skill

[![6000+ Prompts](https://img.shields.io/badge/Prompts-6000%2B-brightgreen)](https://github.com/YouMind-OpenLab/nano-banana-pro-prompts-recommend-skill)
[![Daily Updates](https://img.shields.io/badge/Updates-Twice%20Daily-blue)]()
[![Multi-language](https://img.shields.io/badge/Language-Multi--lingual-orange)]()

> **Stop scrolling Twitter for image prompts!** Let Claude Code intelligently recommend from 6000+ curated image generation prompts based on your needs.
>
> [View Gallery →](https://youmind.com/nano-banana-pro-prompts)

![Demo](public/cover.png)

## The Problem

Every time you need to generate an image — article covers, video thumbnails, infographics — you spend ages searching for the right prompt. Scrolling through Twitter threads, bookmarking posts, copy-pasting... it's exhausting.

## The Solution

Just tell the AI what you want in one sentence:

1. **Smart Search** — Searches through 6000+ prompts organized by use case
2. **Visual Preview** — Every recommendation comes with sample images
3. **Ready to Use** — Get the exact English prompt for Nano Banana Pro model
4. **Content Remix** — Provide your article/video/podcast content, pick a style, get a customized prompt tailored to your content

### Example Conversations

**Direct Search:**
```
"Find me a cartoon-style avatar prompt"
"I need prompts for travel blog covers"
"Help me create an infographic for data comparison"
"Looking for product photography prompts with white background"
```

**Content Illustration (Remix Mode):**
```
"Here's my article about startup lessons learned, help me create a cover image"
"I need an illustration for this podcast episode about AI and creativity: [paste content]"
"Generate a thumbnail for my video script: [paste script]"
```

When you provide content, the skill will:
1. Recommend matching style templates with previews
2. Ask clarifying questions (e.g., gender, age, mood) to personalize
3. Generate a customized prompt based on your content + selected style

## Data Source

- Prompts curated from viral Twitter/X posts by top AI artists
- Updated automatically **twice daily** via GitHub Actions
- Organized into 10+ use case categories (Avatar, Social Media, Product, etc.)

## Installation

### One-liner (Recommended)

```bash
npx skills i YouMind-OpenLab/nano-banana-pro-prompts-recommend-skill
```

Auto-detects all AI assistants (Claude Code, Cursor, Codex, Gemini CLI, Windsurf, etc.) and installs to all of them.

### Alternative: openskills

```bash
# Install
npx openskills install YouMind-OpenLab/nano-banana-pro-prompts-recommend-skill

# Update to latest
npx openskills update nano-banana-pro-prompts-recommend-skill
```

### Alternative: Ask Claude Code

> "Help me install YouMind-OpenLab/nano-banana-pro-prompts-recommend-skill"

### Alternative: Claude Code Plugin Marketplace

```bash
/plugin marketplace add YouMind-OpenLab/nano-banana-pro-prompts-recommend-skill
```

Then enable auto-update in `/plugin` settings for automatic updates.

## Update

### Using skills CLI

```bash
npx skills i YouMind-OpenLab/nano-banana-pro-prompts-recommend-skill
```

Re-running the install command pulls the latest version from GitHub. (`skills update` is planned but not yet available.)

### Using openskills

```bash
npx openskills update nano-banana-pro-prompts-recommend-skill
```

### Using Claude Code Plugin Marketplace

If installed via Plugin Marketplace with auto-update enabled, updates happen automatically.

## Categories

| Category | Prompts | Use Cases |
|----------|---------|-----------|
| Profile / Avatar | 700+ | Headshots, profile pictures, character portraits |
| Social Media Post | 3800+ | Instagram, Twitter, Facebook, viral content |
| Product Marketing | 1900+ | Ads, campaigns, promotional materials |
| Infographic | 350+ | Data visualization, educational content |
| Poster / Flyer | 300+ | Events, announcements, banners |
| E-commerce | 200+ | Product photos, listings, white background |
| Game Asset | 200+ | Sprites, characters, items |
| YouTube Thumbnail | 100+ | Click-worthy video covers |
| Comic / Storyboard | 200+ | Manga, panels, sequential art |
| App / Web Design | 100+ | UI mockups, interface designs |

## Project Structure

```
nano-banana-pro-prompts-recommend-skill/
├── SKILL.md                 # Skill configuration and instructions
├── README.md
├── package.json
├── scripts/
│   └── generate-references.ts   # Fetches data from CMS
├── references/              # Auto-generated JSON files
│   ├── {category}.json      # Category files (search only)
│   └── others.json          # Uncategorized prompts
└── .github/workflows/
    └── generate-references.yml  # Scheduled updates
```

## Development

### Prerequisites

- Node.js 20+
- pnpm

### Setup

```bash
pnpm install

# Create .env with CMS credentials
echo "CMS_HOST=your_host" >> .env
echo "CMS_API_KEY=your_key" >> .env

# Generate references
pnpm run generate
```

### GitHub Actions

Configure repository secrets:

| Secret | Description |
|--------|-------------|
| `CMS_HOST` | PayloadCMS API host |
| `CMS_API_KEY` | PayloadCMS API key |

Runs at 00:00 and 12:00 UTC daily.

## Architecture

Following [Claude Code skill best practices](https://github.com/anthropics/skills):

- **Signal Mapping** — Keyword-to-category routing for efficient search
- **Token Optimization** — Never loads full category files; uses Grep to search
- **Content-Aware Remix** — Extracts themes from user content and personalizes prompts with clarifying questions
- **Graceful Fallback** — If no match found, generates custom prompt with clear AI-generated label

## Related Links

- [skills CLI](https://www.npmjs.com/package/skills) - The "npm" of AI skills by Vercel
- [openskills](https://github.com/nicepkg/openskills) - Universal skills loader
- [anthropics/skills](https://github.com/anthropics/skills) - Official Anthropic skills


## Overview & Purpose

Nano Banana Pro Prompts Recommend Skill is a Claude Code / Cursor skill that helps users discover high‑quality image generation prompts from a curated library of over 6000 examples. It streamlines the process of finding relevant prompts for social media posts, marketing assets, infographics and other creative outputs by offering intelligent recommendations based on user queries.

## Features & Tech Stack

**Key features**

- Smart search across thousands of prompts organized by category.
- Visual previews showing sample images for recommended prompts.
- Ready‑to‑use English prompts tailored for Nano Banana Pro.
- Content remixing to customize prompts based on your own text.
- Scheduled updates via GitHub Actions to ensure the library stays current.

**Tech stack**

| Component | Technology |
| --- | --- |
| Programming language | TypeScript |
| Runtime | Node.js 20+ |
| Package manager | pnpm |
| Automation | GitHub Actions, Claude Code skills CLI |
| Data storage | JSON files generated from PayloadCMS |

## Installation & Usage

To install the skill with the recommended one‑liner, run:

```bash
npx skills i YouMind-OpenLab/nano-banana-pro-prompts-recommend-skill
```

You can also install using the openskills tool:

```bash
npx openskills install YouMind-OpenLab/nano-banana-pro-prompts-recommend-skill
```

After installing, ask your Claude Code or Cursor assistant to search for prompts or provide a piece of text and it will generate a customized image prompt. For local development, clone the repository, run `pnpm install` to install dependencies and `pnpm run generate` to fetch the latest prompt data.

## Business & Entrepreneurial Value

The Nano Banana Pro prompt recommendation engine can be packaged as a premium add‑on to creative suites or workflow automation platforms. By offering a subscription‑based API or licensing the curated prompt library, you can monetize access for marketing teams, social media agencies and businesses seeking to accelerate content creation. The system is designed to scale — the JSON data source can be expanded with new categories and integrated into SaaS platforms via API endpoints. Upsell opportunities include personalized prompt generation services, white‑label licensing and integrations with content management tools.

## Consumer Value

For end users, this skill eliminates the time and frustration of hunting for effective image prompts. Users simply describe what they need and receive ready‑made prompts with visual examples, saving hours of manual research. The ability to remix prompts using their own content offers customization and creative control while maintaining privacy — no sensitive data is stored. Whether you are a blogger, marketer or hobbyist, the skill makes it easy to produce high‑quality visuals that match your style and objectives, leading to better engagement and a more polished final product.

## License

MIT
