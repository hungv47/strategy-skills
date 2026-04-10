# Platform Research Patterns

Search queries and data extraction patterns for content research across platforms.

## Search Query Patterns by Research Goal

### Competitor Content Discovery

| Platform | Query Pattern | Tool |
|----------|--------------|------|
| Blog/Website | `site:[competitor.com] blog` | Exa / Tavily / WebSearch |
| LinkedIn | `from:[company] [topic]` on LinkedIn search | WebFetch (linkedin.com) |
| YouTube | `"[competitor]" [topic]` on YouTube search | Exa with `site:youtube.com` |
| Twitter/X | `from:[handle] [topic]` | WebSearch / Exa |
| Newsletter | `"[competitor] newsletter" OR "[competitor] weekly digest"` | Exa / Tavily |
| Podcast | `"[competitor]" podcast [niche]` | Exa / WebSearch |

### Audience Pain Points

| Platform | Query Pattern | Tool |
|----------|--------------|------|
| Reddit | `"[niche] frustrating" OR "[niche] problem" site:reddit.com` | Exa / Tavily |
| Reddit (questions) | `"how do you" OR "best way to" [niche verb] site:reddit.com` | Exa / Tavily |
| Reddit (wishes) | `"I wish" OR "if only" [niche product] site:reddit.com` | Exa / Tavily |
| Reddit (comparisons) | `"[competitor A] vs [competitor B]" site:reddit.com` | Exa / Tavily |
| Hacker News | `[topic] site:news.ycombinator.com` OR Algolia: `hn.algolia.com/?q=[topic]` | Exa / WebFetch |
| G2 Reviews | `"[product]" site:g2.com/products` | Exa / WebFetch |
| Capterra | `"[product]" site:capterra.com` | Exa / WebFetch |
| App Store | Search via `apps.apple.com/app/[name]` reviews section | WebFetch |
| Stack Overflow | `[technical problem] site:stackoverflow.com` | Exa / WebSearch |

### Trending Topics

| Platform | Method | Tool |
|----------|--------|------|
| Google Trends | `trends.google.com/trending` + keyword comparison | WebFetch |
| Reddit Rising | `reddit.com/r/[subreddit]/rising` | WebFetch |
| TikTok Hashtags | `ads.tiktok.com/business/creativecenter/inspiration/popular/hashtag` | WebFetch |
| YouTube Trending | YouTube Data API `videos.list` with `chart=mostPopular` | API / Exa |
| LinkedIn | `#[niche]` sorted by "Top" in LinkedIn search | WebFetch |

### Switching & Alternative Signals

| Query Pattern | What It Reveals |
|--------------|----------------|
| `"switched from [competitor]"` | Why people leave competitors |
| `"alternative to [competitor]"` | Demand for alternatives + unmet needs |
| `"[competitor] vs" OR "vs [competitor]"` | How audience compares options |
| `"stopped using [competitor]"` | Churn reasons |
| `"looking for [product category]"` | Active buyer language |

## Data Extraction Patterns

### From Blog/Website Content
Extract:
- Title / H1
- Publish date
- Word count (estimate from page length)
- Topic category
- Content format (how-to, listicle, case study, comparison, opinion, guide)
- Social share counts (if visible)
- Internal links (reveals content strategy)

### From Social Media Posts
Extract:
- Post text / hook
- Format (text-only, image, video, carousel, poll)
- Engagement (likes, comments, shares, saves)
- Post date
- Hashtags used
- Comment sentiment (quick scan of top 5-10 comments)

### From Review Platforms
Extract:
- Star rating distribution
- Common themes in 3-star reviews (most balanced)
- "I wish..." patterns
- Comparison mentions ("better than X", "unlike Y")
- Feature requests
- Use-case descriptions (how people actually use the product)

### From Ad Libraries
Extract:
- Hook text (first line / headline)
- Body copy (full message)
- CTA text and type
- Creative format (static / video / carousel)
- Start date → calculate run duration
- Platform placement
- Landing page URL (if visible)

## Engagement Signal Calibration

Context for judging whether engagement is meaningful:

| Platform | Metric | High | Medium | Low |
|----------|--------|------|--------|-----|
| Reddit | Post upvotes | 500+ | 50-499 | <50 |
| Reddit | Comment count | 100+ | 20-99 | <20 |
| Hacker News | Points | 100+ | 20-99 | <20 |
| LinkedIn | Post reactions | 500+ | 50-499 | <50 |
| LinkedIn | Comments | 50+ | 10-49 | <10 |
| YouTube | Views | 50K+ | 5K-49K | <5K |
| YouTube | Like ratio | >95% | 85-95% | <85% |
| Twitter/X | Likes | 1K+ | 100-999 | <100 |
| G2/Capterra | Review mentions | 50+ | 10-49 | <10 |
| App Store | Reviews | 100+ | 20-99 | <20 |

These vary by niche size — adjust for small/niche audiences where 50 upvotes may be top 1%.

## Tool Priority

1. **Exa MCP** — best for semantic content search, finding similar content by meaning
2. **Tavily MCP** — best for structured web search with content extraction, research workflows
3. **WebSearch** — general web search, always available
4. **WebFetch** — direct page access, best for specific URLs (ad libraries, competitor pages)
5. **Platform-specific APIs** — Reddit API, YouTube Data API for structured data access
