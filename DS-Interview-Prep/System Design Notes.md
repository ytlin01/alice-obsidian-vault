# 🟡 System Design Notes

> For DS/MLE roles, system design focuses on ML systems — not just generic SWE architecture.

---

## Design Framework (use for every question)

1. **Problem** — clarify requirements, scale, constraints
2. **Data** — what data exists, how it's stored, how it flows
3. **Model** — what algorithm, how it's trained, offline vs online
4. **Serving** — how predictions are delivered (batch vs real-time)
5. **Monitoring** — how you detect model drift, data issues, failures

---

## Checklist

### Month 1 — Concepts
- [ ] Databases vs data warehouses
- [ ] Batch processing vs streaming
- [ ] APIs & microservices (high level)
- [ ] CAP theorem
- [ ] Caching basics
- [ ] Read DDIA Chapter 1

### Month 2 — ML System Archetypes
- [ ] Recommendation system
- [ ] Feature store (online vs offline)
- [ ] ML training pipeline
- [ ] A/B testing platform
- [ ] Read DDIA Chapter 3

### Month 3 — Full Walkthroughs
- [ ] Design a recommendation system (full)
- [ ] Design a feature store (full)
- [ ] Design an ML pipeline end-to-end
- [ ] Design an A/B testing platform

---

## System Design: Recommendation System

### Problem
Design a system that recommends content to users (e.g. YouTube, Netflix, TikTok).

### Data
- User interaction logs (clicks, watches, skips)
- Item metadata (tags, category, duration)
- User profiles (demographics, history)
- Stored in: data warehouse (Snowflake/BigQuery) + feature store

### Model
- **Candidate generation:** collaborative filtering or two-tower neural net → narrows millions of items to hundreds
- **Ranking:** gradient boosted model or neural ranker → scores candidates
- **Filtering:** business rules (already watched, blocked content)

### Serving
- Batch: pre-compute recommendations nightly, store in Redis
- Real-time: serve from Redis cache, < 100ms latency

### Monitoring
- Track CTR, watch time, diversity metrics
- Monitor feature drift (new users with no history)
- A/B test new models before full rollout

---

## System Design: Feature Store

### Problem
Centralize features so they're consistent between training and serving.

### Components
- **Offline store** (e.g. S3 + Spark) — historical features for training
- **Online store** (e.g. Redis) — low-latency features for serving
- **Feature pipeline** — computes and syncs features between stores

### Key challenge
Training-serving skew — features computed differently offline vs online leads to model degradation.

---

## Key Vocabulary

| Term | Definition |
|------|------------|
| Feature store | Centralized repo for ML features, shared across models |
| Model drift | Model performance degrades as real-world data changes |
| Data pipeline | Automated flow of data from source to destination |
| Batch inference | Run predictions on a large dataset at once (e.g. nightly) |
| Online inference | Real-time predictions per request |
| Cold start | No historical data for a new user or item |
| Two-tower model | Neural net with separate user and item encoders |

---

## Resources
- Eugene Yan's blog: https://eugeneyan.com
- ML System Design GitHub: https://github.com/chiphuyen/machine-learning-systems-design
- DDIA book (chapters 1–3 priority)
