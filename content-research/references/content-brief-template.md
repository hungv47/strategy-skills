# Content Brief Template

Structured format for actionable content briefs that bridge research findings to content-create execution.

## Brief Structure

Each brief should contain ALL of the following fields:

```markdown
### Brief [N]: [Working Title]

- **Topic:** [Specific subject — not vague]
- **Angle:** [What makes ours different — the unique perspective or approach]
- **Format:** [Exact content type: blog post, LinkedIn carousel, TikTok video, email newsletter, etc.]
- **Platform:** [Primary: where it publishes | Secondary: cross-post destinations]
- **Hook approach:** [One of: Question / Bold Claim / Social Proof / How-to / Story / Data / UGC] — based on [cite winning pattern]
- **Key message:** [Core idea in exactly one sentence]
- **Audience language to use:** [3-5 specific phrases from listening research with source]
- **Audience language to avoid:** [Brand jargon the audience doesn't use]
- **Evidence:** [Why this will work — cite specific research findings: ad data, community demand, trend, gap]
- **Competitive positioning:** [What competitors cover / don't cover on this topic]
- **Priority:** [High / Medium] — [One-line justification based on evidence count]
- **Suggested execution:** `content-create` Route [A/B/D] → Channel: [specific channel from 9-channel map]
- **Tracking:** [Suggested UTM: ?utm_source=[platform]&utm_medium=[format]&utm_campaign=[brief-slug]]
```

## Field Guidelines

### Topic
Bad: "AI code review"
Good: "Why 2000+ line PRs are killing your engineering velocity — and what to do about it"

### Angle
The angle is what makes this content worth creating despite competitor coverage. It should reference a specific gap, trend, or audience need from research.

Bad: "We'll write about code review"
Good: "Multi-repo context awareness angle — no competitor covers this, and 15 Reddit threads in r/ExperiencedDevs discuss it"

### Format Selection
Match format to platform and content type:

| Content Goal | Best Formats | Best Platforms |
|-------------|-------------|---------------|
| Awareness / reach | Short video, carousel, infographic | TikTok, LinkedIn, Instagram |
| Thought leadership | Long-form post, blog, video essay | LinkedIn, Blog, YouTube |
| SEO / evergreen | Blog post, guide, comparison | Website blog |
| Lead generation | Gated guide, calculator, template | Blog + landing page |
| Community engagement | Discussion post, AMA, thread | Reddit, Twitter/X, LinkedIn |
| Email nurture | Newsletter, case study digest | Email |

### Hook Approach
Choose based on research findings — not preference:

| Hook Type | When to Use | Example |
|-----------|------------|---------|
| **Question** | Audience actively asking this question | "Why do your PRs take 3 days to review?" |
| **Bold Claim** | Data supports a counterintuitive position | "Most AI code review tools miss 80% of what matters" |
| **Social Proof** | User testimonials / metrics available | "How [Company] cut PR review time by 60%" |
| **How-to** | Audience searching for solutions | "How to review PRs 10x faster without missing bugs" |
| **Story** | Emotional resonance strong in community | "I spent 3 hours reviewing a 2000-line PR. Here's what happened." |
| **Data** | Quantified insight available | "78% of developers now use AI coding tools. Here's what they're missing." |
| **UGC** | Authentic voice outperforms brand voice | Real user walkthrough / testimonial |

### Audience Language
Pull directly from listening-agent output. Include the exact phrase, source, and usage context.

Bad: "Users are frustrated with slow reviews"
Good:
- Use: "review tax" (r/ExperiencedDevs, 340 upvotes)
- Use: "PR bottleneck" (15 threads across r/programming)
- Avoid: "automated code quality analysis" (brand jargon — 0 organic usage)

### Evidence
Every brief must cite at least 2 research findings. The strength of evidence determines priority:

| Priority | Evidence Required |
|----------|------------------|
| **High** | 3+ signals: ad spend + community demand + gap + trend |
| **Medium** | 2 signals from different research dimensions |

### content-create Route Mapping

| Brief Type | content-create Route | When |
|-----------|---------------------|------|
| Quick social post | Route A (Single Asset/Quick) | One-off post, simple format |
| Full campaign asset | Route B (Full Asset/Campaign) | Blog, video script, comprehensive piece |
| Channel-specific | Route D (Channel-Specific) | Platform-native content (Reddit, newsletter, etc.) |

## Prioritization Summary Table

After all briefs, include:

```markdown
## Brief Prioritization Summary

| # | Brief | Priority | Evidence Signals | Est. Effort | Expected Impact |
|---|-------|----------|-----------------|-------------|----------------|
| 1 | [Title] | High | 4 signals (ad + community + gap + trend) | Medium | [Specific expected outcome] |
| 2 | [Title] | High | 3 signals (community + gap + format) | Low | [Outcome] |
| 3 | [Title] | Medium | 2 signals (trend + gap) | High | [Outcome] |
```

## Common Mistakes

1. **Vague topics** — "Write about AI" is not a brief. Specify the exact angle.
2. **Missing audience language** — If the brief doesn't include specific phrases from listening research, it's not research-informed.
3. **No evidence** — "This seems like a good idea" is not evidence. Cite the data.
4. **Wrong format for platform** — Long-form blog post on TikTok doesn't work. Match format to platform.
5. **No execution path** — Every brief must map to a content-create route and channel.
6. **Copying competitor angles** — The point is to find what's DIFFERENT, not replicate.
