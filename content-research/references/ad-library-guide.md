# Ad Library Access Guide

How to access and interpret advertising transparency data across major platforms.

## Platform Access Matrix

| Platform | URL | Auth Required | API Available | Data Quality |
|----------|-----|--------------|--------------|-------------|
| Meta (Facebook + Instagram) | `facebook.com/ads/library` | No | Limited (EU political only) | Good — all active ads visible |
| TikTok Creative Center | `ads.tiktok.com/business/creativecenter` | No | No official API | Good — curated top ads with CTR data |
| LinkedIn | `linkedin.com/ad-library` | No | No official API | Good — all active ads by company |
| Google Ads | `adstransparency.google.com` | No | No | Moderate — search/display ads visible |
| YouTube | Via Google Ads Transparency | No | YouTube Data API (videos) | Moderate |

## Meta Ad Library

### Access
- Navigate to `facebook.com/ads/library`
- No login required for browsing
- Search by advertiser name, keyword, or page name
- Filter by: country, platform (Facebook/Instagram), media type (image/video/meme), active status, date range

### Key Data Points
- **Ad creative:** Full text, images, or video
- **Start date:** When the ad began running → calculate run duration
- **Active status:** Currently running or stopped
- **Platforms:** Facebook, Instagram, Messenger, Audience Network
- **Multiple versions:** Many ads have A/B variants visible

### Performance Proxy: Run Duration
- **3-7 days:** Testing phase — inconclusive
- **7-30 days:** Early signal — may be performing
- **30-60 days:** Strong signal — likely profitable
- **60+ days:** High confidence — almost certainly profitable
- **Stopped after <7 days:** Likely underperformed

### Search Patterns
```
# Direct competitor search
Search: "[Competitor Name]" → shows all their ads

# Keyword search (finds ads mentioning topic)
Search: "[product category keyword]"

# Filter for insights
- Set date range to "Last 90 days"
- Filter by "Active" to see what's currently running
- Toggle between platforms to see channel-specific creative
```

## TikTok Creative Center

### Access
- Navigate to `ads.tiktok.com/business/creativecenter`
- No login required for browsing
- Sections: Top Ads Dashboard, Keyword Insights, Hashtag trends, Song trends

### Top Ads Dashboard
- Filter by: industry, region, objective (traffic/conversions/app install), duration, format
- Shows: CTR range, engagement metrics, video preview
- **Best use:** Filter by your industry → sort by CTR → analyze top 20 ads

### Keyword Insights
- Shows which keywords appear in high-performing TikTok ads
- Includes CTR data per keyword
- **Best use:** Search your niche keywords → see which have highest CTR in ad copy

### Key TikTok Creative Benchmarks (2025-2026)
- Average CTR: 0.8-1.1%
- Top 10% ads: 2.5%+ CTR
- Hook rate (3-second view): should be >30%
- Average high-performing creative lifespan: 7-10 days before fatigue
- Native/lo-fi UGC style dramatically outperforms polished TV-style content

## LinkedIn Ad Library

### Access
- Navigate to `linkedin.com/ad-library`
- Search by company name or keyword
- Filter by: country, date range

### Key Data Points
- **Ad type:** Image, video, document, carousel, event
- **Headline and body copy:** Full text visible
- **Creative assets:** Viewable but not always downloadable
- **Advertiser:** Company page linked

### B2B-Specific Value
- LinkedIn ad library is specifically valuable for B2B because brands test professional messaging here that doesn't appear elsewhere
- Long-running LinkedIn ads are reliable signals of what resonates with professional audiences
- Check both company page ads AND individual exec/founder promoted posts

## Google Ads Transparency Center

### Access
- Navigate to `adstransparency.google.com`
- Search by advertiser name
- Filter by: region, date range, format (text/image/video)

### Key Data Points
- **Search ads:** Headlines, descriptions, display URLs
- **Display ads:** Banner creatives across Google Display Network
- **YouTube ads:** Video ad creatives
- **Date range:** When ads were shown

## Cross-Platform Analysis Framework

When analyzing ads across platforms, extract and compare:

1. **Hook pattern:** How do they open? (Question/Claim/Social proof/Story/Data)
2. **Value proposition:** What do they promise?
3. **CTA:** What action do they ask for? (Free trial/Demo/Download/Learn more)
4. **Format:** What creative format dominates? (Static/Video/Carousel/UGC)
5. **Tone:** Professional/Casual/Urgent/Educational?
6. **Objection handling:** Do they address concerns proactively?
7. **Social proof:** Reviews, logos, metrics, testimonials?
8. **Destination:** Where does the ad send traffic? (Landing page/Product page/Blog/Free tool)

## Third-Party Ad Intelligence Tools

When platform ad libraries don't provide enough data:

- **AdLibrary.com** — Unified API covering Meta, TikTok, LinkedIn, Google, YouTube. Simple API key auth. Returns headline, body, creative URLs, landing pages, CTA text, run dates.
- **Apify scrapers** — Platform-specific scraping Actors for TikTok Creative Center top ads, YouTube ads, etc. Via Apify MCP if installed.
- **SociaVault** — Multi-platform API covering TikTok, Instagram, YouTube, Facebook, Reddit, LinkedIn.

Use these when:
- Direct platform access is blocked or rate-limited
- You need structured data for bulk analysis
- You need historical data beyond what's currently active
