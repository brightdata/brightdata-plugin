<p align="center">
  <img src="https://brightdata.com/wp-content/themes/brightdata/assets/images/favicon.png" alt="Bright Data" width="80" height="80">
</p>

<h1 align="center">Bright Data Plugin for Claude Code</h1>

<p align="center">
  <strong>Unlock the web with AI-powered scraping and search</strong>
</p>

<p align="center">
  <a href="https://brightdata.com"><img src="https://img.shields.io/badge/Powered%20by-Bright%20Data-3D7FFC?style=for-the-badge" alt="Powered by Bright Data"></a>
  <a href="#license"><img src="https://img.shields.io/badge/License-MIT-10b981?style=for-the-badge" alt="MIT License"></a>
  <a href="#skills"><img src="https://img.shields.io/badge/Skills-2-9D97F4?style=for-the-badge" alt="2 Skills"></a>
</p>

<p align="center">
  <a href="#-quick-start">Quick Start</a> •
  <a href="#-skills">Skills</a> •
  <a href="#-setup">Setup</a> •
  <a href="#-usage">Usage</a> •
  <a href="#-examples">Examples</a>
</p>

---

## Overview

This plugin brings **Bright Data's powerful web infrastructure** directly into Claude Code, enabling AI agents to:

- **Scrape any webpage** as clean markdown — bypassing bot detection, CAPTCHAs, and JavaScript rendering
- **Search Google** with structured JSON results — titles, links, and descriptions ready for processing

Built on Bright Data's [Web Unlocker](https://brightdata.com/products/web-unlocker) and [SERP API](https://brightdata.com/products/serp-api), this plugin handles the complexity of web access so your AI agents can focus on what matters.

---

## Skills

| Skill | Description |
|-------|-------------|
| **`search`** | Search Google and get structured JSON results with titles, links, and descriptions |
| **`scrape`** | Scrape any webpage as clean markdown with automatic bot detection bypass |

---

## Quick Start

### 1. Get Your Credentials

1. Sign up at [brightdata.com](https://brightdata.com) if you haven't already
2. Go to the [Bright Data Dashboard](https://brightdata.com/cp)
3. Create a **Web Unlocker zone**: Click "Add" → Select "Unlocker zone"
4. Copy your **API Key** from the dashboard

### 2. Set Environment Variables

```bash
export BRIGHTDATA_API_KEY="your-api-key"
export BRIGHTDATA_UNLOCKER_ZONE="your-zone-name"
```

### 3. Start Using

```bash
# Search Google
bash skills/search/scripts/search.sh "artificial intelligence trends"

# Scrape a webpage
bash skills/scrape/scripts/scrape.sh "https://example.com/article"
```

---

## Setup

### Prerequisites

| Dependency | Version | Description |
|------------|---------|-------------|
| `curl` | ≥ 7.0 | HTTP client for API requests |
| `jq` | ≥ 1.5 | JSON processor for parsing responses |

**Install on Ubuntu/Debian:**
```bash
sudo apt-get install curl jq
```

**Install on macOS:**
```bash
brew install curl jq
```

### Environment Variables

| Variable | Required | Description |
|----------|----------|-------------|
| `BRIGHTDATA_API_KEY` | Yes | Your Bright Data API key from the [dashboard](https://brightdata.com/cp) |
| `BRIGHTDATA_UNLOCKER_ZONE` | Yes | Name of your Web Unlocker zone |

---

## Usage

### Search Skill

Search Google and receive structured JSON results.

```bash
bash skills/search/scripts/search.sh "query" [page]
```

**Parameters:**
| Parameter | Required | Default | Description |
|-----------|----------|---------|-------------|
| `query` | Yes | - | Search query string |
| `page` | No | `0` | Page number (0-indexed) for pagination |

**Output Format:**
```json
{
  "organic": [
    {
      "link": "https://example.com/result",
      "title": "Result Title",
      "description": "Brief description of the page..."
    }
  ]
}
```

### Scrape Skill

Scrape any webpage and get clean markdown content.

```bash
bash skills/scrape/scripts/scrape.sh "url"
```

**Parameters:**
| Parameter | Required | Description |
|-----------|----------|-------------|
| `url` | Yes | Full URL of the page to scrape |

**Features:**
- Automatic bot detection bypass
- CAPTCHA solving
- JavaScript rendering
- Clean markdown output

---

## Examples

### Research Task
```bash
# Search for recent news
bash skills/search/scripts/search.sh "climate change 2024"

# Get full article content
bash skills/scrape/scripts/scrape.sh "https://example.com/climate-article"
```

### Competitive Analysis
```bash
# Find competitor pages
bash skills/search/scripts/search.sh "best project management tools"

# Scrape product details
bash skills/scrape/scripts/scrape.sh "https://competitor.com/pricing"
```

### Content Aggregation
```bash
# Search for tutorials
bash skills/search/scripts/search.sh "python web scraping tutorial" 0

# Get page 2
bash skills/search/scripts/search.sh "python web scraping tutorial" 1
```

---

## Project Structure

```
brightdata-plugin/
├── .claudeplugin/
│   └── plugin.json          # Plugin configuration
├── skills/
│   ├── search/
│   │   ├── SKILL.md         # Search skill documentation
│   │   └── scripts/
│   │       └── search.sh    # Google search implementation
│   └── scrape/
│       ├── SKILL.md         # Scrape skill documentation
│       └── scripts/
│           └── scrape.sh    # Web scraper implementation
├── README.md
└── LICENSE
```

---

## API Reference

Both skills use the Bright Data Request API:

```
POST https://api.brightdata.com/request
Authorization: Bearer <BRIGHTDATA_API_KEY>
Content-Type: application/json

{
  "url": "<target_url>",
  "zone": "<BRIGHTDATA_UNLOCKER_ZONE>",
  "format": "raw",
  "data_format": "markdown" | "parsed_light"
}
```

| data_format | Used by | Description |
|-------------|---------|-------------|
| `parsed_light` | Search | Returns structured SERP data |
| `markdown` | Scrape | Returns page content as markdown |

---

## Troubleshooting

### "BRIGHTDATA_API_KEY is not set"
Ensure you've exported the environment variable:
```bash
export BRIGHTDATA_API_KEY="your-api-key"
```

### "BRIGHTDATA_UNLOCKER_ZONE is not set"
Create a Web Unlocker zone in your [dashboard](https://brightdata.com/cp) and export it:
```bash
export BRIGHTDATA_UNLOCKER_ZONE="your-zone-name"
```

### Empty or malformed results
- Verify your API key is valid
- Check that your zone is active and properly configured
- Ensure `jq` is installed for JSON processing

---

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## Links

- [Bright Data](https://brightdata.com) - Official website
- [Documentation](https://docs.brightdata.com) - API documentation
- [Dashboard](https://brightdata.com/cp) - Manage your account
- [Web Unlocker](https://brightdata.com/products/web-unlocker) - Learn about Web Unlocker
- [SERP API](https://brightdata.com/products/serp-api) - Learn about SERP API

---

<p align="center">
  <sub>Built with the power of <a href="https://brightdata.com">Bright Data</a></sub>
</p>
