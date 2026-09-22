# Web Service BM (Business Model) Reference

Used by the Web-BM skill, and by Web-Plan's BM section.

## Common web service revenue models

| Model | Core idea | Good fit for | Risk |
|---|---|---|---|
| Subscription (SaaS) | Flat monthly/annual fee | Tools/services that deliver value repeatedly | Growth stalls if early users don't convert to paid |
| Freemium | Free core + paid advanced features | Needs to build a user base first | Free tier too generous → no reason to upgrade |
| Transaction fee (marketplace) | % cut on completed transactions | Supply-demand matching services | Cold-start problem on both sides of the market early on |
| Advertising | Revenue from traffic-based impressions/clicks | Services that can pull large free traffic | Small traffic makes this revenue effectively meaningless |
| Lead / data connection | Connects user inquiries to partner companies | B2B matching, comparison services | Privacy/trust concerns, check legal exposure |
| One-time purchase | Single purchase of a tool/template/asset | Low-frequency-use tools, small projects | Low LTV, not a recurring revenue structure |

Combining several is more common in practice than picking just one (e.g. freemium + ads).

## Questions to ask when designing pricing

- What are similar services charging (use Web-DeepSearch to find out if unknown)?
- What is the target user spending money on right now for this same problem (the cost of existing alternatives anchors the price)?
- What triggers conversion from the free tier (usage caps? advanced features? team features?)?

## Minimum metrics to state

Full financial modeling isn't necessary, but the plan should state at least the following, in numbers or direction:

- **Conversion target**: what % free-to-paid conversion is the goal
- **Core revenue metric(s)**: 1-2 metrics to track (MRR, ARPU, etc.)
- **Rough break-even sense**: roughly how many paying users/transactions are needed to cover operating cost (doesn't need to be precise, but should be right in order of magnitude)
