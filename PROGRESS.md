# MarketPulse progress

## Phase 0: setup checklist (waiting on the owner)

- [ ] v0.1 code pushed to the repo (the repo was empty when work started)
- [ ] Supabase project (Mumbai, ap-south-1); pgvector enabled
- [ ] Groq API key; free-tier limits checked in the console
- [ ] Google AI Studio key (Gemini overflow)
- [ ] Resend account and API key
- [ ] Render account linked to GitHub (needed in Phase 5)
- [ ] Vercel project for `web/` (needed in Phase 7)
- [ ] LangSmith key (optional)
- [ ] GitHub Actions secrets (needed in Phase 4)
- [ ] Decision: Supabase new API keys + JWKS JWT verification (see below)

### Changes to the plan, waiting for approval

1. **Supabase keys.** Supabase is replacing the legacy `anon` / `service_role` keys and the
   shared JWT secret with publishable (`sb_publishable_…`) and secret (`sb_secret_…`) keys and
   asymmetric JWT signing keys; the legacy keys are due to be deprecated by the end of 2026.
   Proposal: use `SUPABASE_PUBLISHABLE_KEY` / `SUPABASE_SECRET_KEY` and verify user JWTs against
   the project's JWKS endpoint, dropping `SUPABASE_JWT_SECRET`.
2. **DATABASE_URL** uses the shared pooler in **session mode (port 5432)**. GitHub Actions and
   Render are IPv4-only, the direct host is IPv6-only on the free plan, and session mode keeps
   prepared statements working for `PostgresSaver`.

## Phase log

| Phase | Status | Commit | Notes |
| --- | --- | --- | --- |
| 0 | waiting on owner | | checklist given |
