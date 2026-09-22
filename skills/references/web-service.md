# Web Service Plan Structure

Use the sections below as the default skeleton. Skip sections that don't fit the project's scale — sections 7-8 are often skipped for personal projects/early MVPs in particular.

## 1. Service Overview
- One-line definition: who it's for, what it solves, and how
- Problem statement: what pain the target user has right now without this service (and the limits of any existing alternative, if one exists)
- Core value proposition: one sentence on why someone would use this

## 2. Target Users
- Primary persona (age range, situation, need — "what situation is this person in" matters more than raw demographics)
- 1-2 concrete usage scenarios (e.g. "a streamer pulling highlight clips right after a broadcast ends")
- (BM assumption) Note in one line here whether this target is the one who actually pays, or whether there's a separate paying party (e.g. advertisers) — flesh this out in section 8.

## 3. Core Features (Priority)
Lay out as a table:

| Feature | Description | Priority (Must/Should/Could) | Notes |
|---|---|---|---|
| | | | |

Clearly separate what the MVP absolutely needs from what's nice-to-have and can wait. When priority is unclear, use the test: "does the core value proposition still hold without this feature?"

## 4. User Flow
List the screen-to-screen flow in order for each major scenario.
Example: Landing → Sign-up → Onboarding → Use core feature → View/share result

Call out any point where users are likely to drop off (complex input, waiting, checkout, etc.).

## 5. Information Architecture / Screen Structure
Lay out major screens and sub-screens hierarchically, like a sitemap.
```
Home
├── Dashboard
├── Projects
│   ├── Project Detail
│   └── Settings
└── My Page
```

## 6. Feature Specification
For each core feature, fill in:
- **User story**: "As a ___, I want to ___, because ___."
- **Acceptance criteria**: the concrete bar for "this feature is done" (checklist form is best)

## 7. Non-Functional Requirements
Cover only what actually matters for this project — not every service needs all of these.
- Performance: response time targets, concurrent-user handling
- Security: auth/authorization model, how sensitive data is handled
- Scalability: how much headroom is needed for traffic/data growth

## 8. Monetization / Business Model
Give this section weight equal to or greater than the others — if the service exists to make money, BM should be the standard that drives feature priority, not an afterthought. Compare 2-3 candidate models and record the reasoning for the recommendation (see `bm-web.md` for model types). Use the Web-BM skill when this needs to go deeper (pricing, conversion funnel, metrics).

- **Revenue model**: how it makes money, or — if monetization isn't the goal — what "success" means for this project instead
- **Pricing / conversion point**: if there's a free-to-paid boundary, where the conversion is triggered
- **Core revenue metric(s)**: 1-2 metrics this service should track (MRR, ARPU, etc.)

## 9. Success Metrics (KPIs)
What tells you this service is working.
Example: sign-up conversion rate, return rate (WAU/MAU), core-feature usage rate, completion rate

## 10. Competitors / Similar Services
Mention 2-3 if they exist, and briefly note where this service differentiates. Skip if there's nothing comparable.
