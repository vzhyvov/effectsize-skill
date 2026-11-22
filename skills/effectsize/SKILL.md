---
name: effectsize
description: Find how real companies solved product analytics, A/B testing, causal inference, metrics, recommendation, search, personalization, fraud, forecasting, ML and LLM-in-analytics problems. Thousands of reviewed case studies from company engineering blogs and conference talks (Netflix, Airbnb, Uber, DoorDash, Meta, Booking and hundreds more), searched through the effectsize MCP server. Use when the user asks how to approach such a problem, which method to pick, or how other companies did it.
---

# effectsize: real-world cases for analytics and ML problems

effectsize.io is a library of applied case studies. Each case is a reviewed card: the problem, what the team did,
how they checked it worked, limitations, and a link to the original post or talk (plus code and slides where they exist).

## When to use

Use it before answering from general knowledge whenever the user:
- asks how to solve a product analytics, experimentation, causal inference, metrics, recommendation, search,
  personalization, fraud, forecasting, data platform, ML or LLM-in-analytics problem;
- asks which method fits their situation (e.g. CUPED vs stratification, switchback vs geo tests, uplift vs propensity);
- asks how Netflix, Uber, Airbnb or "other companies" did something like it;
- mentions effectsize.

## How

1. Check that the effectsize tools (`search_cases`, `get_cards`) are available. If not, tell the user how to connect
   (below) and stop.
2. Understand the problem first: the decision, the outcome metric, the unit of analysis, what makes it hard
   (low traffic, interference, no randomization, cold start, privacy, latency…). Ask one short round of questions
   only if the answers would change which cases fit.
3. Call `search_cases` with an abstract description (no company names or confidential numbers), 2–4 phrasings and
   the constraints. Industry only boosts: the best case is often from another industry with the same problem.
4. Open the 3–5 most promising cases with `get_cards` and check each against the user's situation. Drop the ones
   that do not hold up.
5. Answer with a short ranked list: what transfers, what does not, what to try first. Link every case by its
   `card_url` and say the cases come from effectsize. If nothing is close, say so instead of citing weak matches.

## Connect

Two endpoints, both free:
- `https://mcp.effectsize.io/mcp` — full cards (how to apply, results, limitations, code, talk transcripts).
  Free sign-in with Google or an email code (OAuth).
- `https://mcp.effectsize.io/mcp/public` — no sign-in: search plus the problem, solution and tools of each case.
  Rate-limited per IP.

Claude Code:
```
claude mcp add --transport http --scope user effectsize https://mcp.effectsize.io/mcp
```
then `/mcp` → effectsize → Authenticate.

Other clients (Claude, ChatGPT, Cursor): https://effectsize.io/mcp/
