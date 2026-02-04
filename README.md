<p align="center">
  <img src="https://brightdata.com/wp-content/themes/brightdata/assets/images/favicon.png" alt="Bright Data" width="80" height="80">
</p>

<h1 align="center">Bright Data Plugin for Claude Code</h1>

<p align="center">
  <strong>Unlock the web with AI-powered scraping, search, and structured data</strong>
</p>

<p align="center">
  <a href="https://brightdata.com"><img src="https://img.shields.io/badge/Powered%20by-Bright%20Data-3D7FFC?style=for-the-badge" alt="Powered by Bright Data"></a>
  <a href="#license"><img src="https://img.shields.io/badge/License-MIT-10b981?style=for-the-badge" alt="MIT License"></a>
  <a href="#skills"><img src="https://img.shields.io/badge/Skills-3-9D97F4?style=for-the-badge" alt="3 Skills"></a>
  <a href="#data-feeds-skill"><img src="https://img.shields.io/badge/Datasets-40+-15C1E6?style=for-the-badge" alt="40+ Datasets"></a>
</p>

<p align="center">
  <a href="#-quick-start">Quick Start</a> •
  <a href="#-skills">Skills</a> •
  <a href="#-data-feeds">Data Feeds</a> •
  <a href="#-setup">Setup</a> •
  <a href="#-examples">Examples</a>
</p>

---

## Overview

This plugin brings **Bright Data's powerful web infrastructure** directly into Claude Code, enabling AI agents to:

- **Scrape any webpage** as clean markdown — bypassing bot detection, CAPTCHAs, and JavaScript rendering
- **Search Google** with structured JSON results — titles, links, and descriptions ready for processing
- **Extract structured data** from 40+ websites — Amazon, LinkedIn, Instagram, TikTok, YouTube, and more

Built on Bright Data's [Web Unlocker](https://brightdata.com/products/web-unlocker), [SERP API](https://brightdata.com/products/serp-api), and [Web Data APIs](https://brightdata.com/products/web-scraper), this plugin handles the complexity of web access so your AI agents can focus on what matters.

---

## Skills

| Skill | Description |
|-------|-------------|
| **`search`** | Search Google and get structured JSON results with titles, links, and descriptions |
| **`scrape`** | Scrape any webpage as clean markdown with automatic bot detection bypass |
| **`data-feeds`** | Extract structured data from 40+ websites with automatic polling |

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

# Get LinkedIn profile data
bash skills/data-feeds/scripts/datasets.sh linkedin_person_profile "https://linkedin.com/in/satyanadella"
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
| `BRIGHTDATA_UNLOCKER_ZONE` | Yes* | Name of your Web Unlocker zone (*required for search/scrape) |
| `BRIGHTDATA_POLLING_TIMEOUT` | No | Max seconds to wait for data-feeds (default: 600) |

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

**Features:**
- Automatic bot detection bypass
- CAPTCHA solving
- JavaScript rendering
- Clean markdown output

### Data Feeds Skill

Extract structured data from 40+ supported websites.

```bash
bash skills/data-feeds/scripts/datasets.sh <dataset_type> <url> [params...]
```

Run without arguments to see all available datasets:
```bash
bash skills/data-feeds/scripts/datasets.sh
```

---

## Data Feeds

### E-Commerce

| Dataset | Command | Description |
|---------|---------|-------------|
| Amazon Product | `datasets.sh amazon_product <url>` | Product details, pricing, ratings |
| Amazon Reviews | `datasets.sh amazon_product_reviews <url>` | Customer reviews |
| Amazon Search | `datasets.sh amazon_product_search <keyword> <domain>` | Search results |
| Walmart Product | `datasets.sh walmart_product <url>` | Product details |
| eBay Product | `datasets.sh ebay_product <url>` | Listing details |
| Best Buy | `datasets.sh bestbuy_products <url>` | Product info |
| Etsy | `datasets.sh etsy_products <url>` | Listing data |
| Home Depot | `datasets.sh homedepot_products <url>` | Product data |
| Zara | `datasets.sh zara_products <url>` | Product details |

### Professional Networks

| Dataset | Command | Description |
|---------|---------|-------------|
| LinkedIn Person | `datasets.sh linkedin_person_profile <url>` | Profile, experience, skills |
| LinkedIn Company | `datasets.sh linkedin_company_profile <url>` | Company page data |
| LinkedIn Jobs | `datasets.sh linkedin_job_listings <url>` | Job posting details |
| LinkedIn Posts | `datasets.sh linkedin_posts <url>` | Post content |
| Crunchbase | `datasets.sh crunchbase_company <url>` | Funding, employees |
| ZoomInfo | `datasets.sh zoominfo_company_profile <url>` | Company profile |

### Social Media

| Dataset | Command | Description |
|---------|---------|-------------|
| Instagram Profiles | `datasets.sh instagram_profiles <url>` | Bio, followers |
| Instagram Posts | `datasets.sh instagram_posts <url>` | Post details |
| Instagram Reels | `datasets.sh instagram_reels <url>` | Reel metrics |
| TikTok Profiles | `datasets.sh tiktok_profiles <url>` | Creator data |
| TikTok Posts | `datasets.sh tiktok_posts <url>` | Video details |
| TikTok Shop | `datasets.sh tiktok_shop <url>` | Product data |
| Facebook Posts | `datasets.sh facebook_posts <url>` | Post content |
| Facebook Marketplace | `datasets.sh facebook_marketplace_listings <url>` | Listings |
| X (Twitter) | `datasets.sh x_posts <url>` | Tweet data |
| YouTube Profiles | `datasets.sh youtube_profiles <url>` | Channel data |
| YouTube Videos | `datasets.sh youtube_videos <url>` | Video details |
| YouTube Comments | `datasets.sh youtube_comments <url> [num]` | Comments |
| Reddit Posts | `datasets.sh reddit_posts <url>` | Post data |

### Other

| Dataset | Command | Description |
|---------|---------|-------------|
| Google Maps Reviews | `datasets.sh google_maps_reviews <url> [days]` | Business reviews |
| Google Shopping | `datasets.sh google_shopping <url>` | Product comparison |
| Google Play Store | `datasets.sh google_play_store <url>` | App details |
| Apple App Store | `datasets.sh apple_app_store <url>` | iOS app data |
| Yahoo Finance | `datasets.sh yahoo_finance_business <url>` | Stock data |
| Zillow | `datasets.sh zillow_properties_listing <url>` | Property listings |
| Booking.com | `datasets.sh booking_hotel_listings <url>` | Hotel data |
| Reuters News | `datasets.sh reuter_news <url>` | Article content |
| GitHub | `datasets.sh github_repository_file <url>` | Repository file |

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
# Get competitor product data
bash skills/data-feeds/scripts/datasets.sh amazon_product "https://amazon.com/dp/B09V3KXJPB"

# Get company info
bash skills/data-feeds/scripts/datasets.sh linkedin_company_profile "https://linkedin.com/company/openai"
```

### Social Media Monitoring
```bash
# Get Instagram profile
bash skills/data-feeds/scripts/datasets.sh instagram_profiles "https://instagram.com/natgeo"

# Get YouTube video stats
bash skills/data-feeds/scripts/datasets.sh youtube_videos "https://youtube.com/watch?v=dQw4w9WgXcQ"
```

### Lead Generation
```bash
# Get LinkedIn profile
bash skills/data-feeds/scripts/datasets.sh linkedin_person_profile "https://linkedin.com/in/satyanadella"

# Get company funding data
bash skills/data-feeds/scripts/datasets.sh crunchbase_company "https://crunchbase.com/organization/openai"
```

---

## Project Structure

```
brightdata-plugin/
├── .claudeplugin/
│   └── plugin.json              # Plugin configuration
├── skills/
│   ├── search/
│   │   ├── SKILL.md             # Search skill documentation
│   │   └── scripts/
│   │       └── search.sh        # Google search implementation
│   ├── scrape/
│   │   ├── SKILL.md             # Scrape skill documentation
│   │   └── scripts/
│   │       └── scrape.sh        # Web scraper implementation
│   └── data-feeds/
│       ├── SKILL.md             # Data feeds documentation
│       └── scripts/
│           ├── datasets.sh      # Dataset wrapper (40+ sources)
│           └── fetch.sh         # Core polling logic
├── README.md
└── LICENSE
```

---

## API Reference

### Search & Scrape (Web Unlocker API)

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

### Data Feeds (Web Data API)

```
POST https://api.brightdata.com/datasets/v3/trigger?dataset_id=<id>
Authorization: Bearer <BRIGHTDATA_API_KEY>
Content-Type: application/json

[{"url": "<target_url>"}]
```

Then poll for results:
```
GET https://api.brightdata.com/datasets/v3/snapshot/<snapshot_id>?format=json
```

---

## Troubleshooting

### "BRIGHTDATA_API_KEY is not set"
```bash
export BRIGHTDATA_API_KEY="your-api-key"
```

### "BRIGHTDATA_UNLOCKER_ZONE is not set"
Create a Web Unlocker zone in your [dashboard](https://brightdata.com/cp):
```bash
export BRIGHTDATA_UNLOCKER_ZONE="your-zone-name"
```

### Data feeds timing out
Increase the polling timeout:
```bash
export BRIGHTDATA_POLLING_TIMEOUT=900
```

### Empty or malformed results
- Verify your API key is valid
- Check that your zone is active
- Ensure `jq` is installed

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
- [Web Data APIs](https://brightdata.com/products/web-scraper) - Learn about Web Data APIs

---

<p align="center">
  <sub>Built with the power of <a href="https://brightdata.com">Bright Data</a></sub>
</p>
