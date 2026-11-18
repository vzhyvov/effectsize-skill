# effectsize skill and MCP server

Give your AI agent 1,300+ real-world case studies of how companies solved product analytics, A/B testing, causal
inference, recommendation, search, fraud, forecasting, ML and LLM-in-analytics problems. Ask a question, and the
agent answers with what actually worked at Netflix, Airbnb, Uber, DoorDash, Meta and hundreds of other companies,
with a link to each case and its original post or talk.

Cases come from [effectsize.io](https://effectsize.io): company engineering blogs, papers and conference talks
(many not in English), each reviewed and turned into a short English card.

## Try it without signing in

Add this MCP server to any client that supports remote MCP (Streamable HTTP):

```
https://mcp.effectsize.io/mcp/public
```

Search works fully; each case returns its problem, solution and tools. For full cards (how to apply, results,
limitations, code, talk transcripts) use the main endpoint below with a free sign-in.

## Install

**Claude Code** — the plugin adds the skill and the MCP server:

```
/plugin marketplace add vzhyvov/effectsize-skill
/plugin install effectsize@effectsize
```

Or just the MCP server:

```
claude mcp add --transport http --scope user effectsize https://mcp.effectsize.io/mcp
```

Then `/mcp` → effectsize → Authenticate (Google or an email code).

**Cursor** — `mcp.json`:

```json
{ "mcpServers": { "effectsize": { "url": "https://mcp.effectsize.io/mcp" } } }
```

**Claude, ChatGPT and other clients** — step-by-step guide: https://effectsize.io/mcp/

**Other agents that read skills** — copy [`skills/effectsize/SKILL.md`](skills/effectsize/SKILL.md) into your
client's skills folder.

## Ask

Start with "Use effectsize:" so the agent searches the cases instead of answering from memory:

- *Use effectsize: we can't randomize users for a pricing change. How did others measure the effect?*
- *Use effectsize: our A/B tests take too long on low traffic. What variance reduction worked in practice?*
- *Use effectsize: how do marketplaces evaluate and improve search ranking?*

## Tools

| Tool | What it does |
|---|---|
| `search_cases` | Finds cases for an abstract description of the problem, its constraints and candidate methods. Deterministic search, no LLM on the server. |
| `get_cards` | Reads up to 5 cases: problem, solution, tools (public); core idea, how to apply, results, limitations, code, talk transcript (signed in). |

Server card: https://mcp.effectsize.io/.well-known/mcp/server-card.json

## Privacy

Search arguments are logged to improve coverage, with a pseudonymous user id; don't send company names or
confidential data (the agent is told to keep queries abstract). Details: https://effectsize.io/privacy/

## License

MIT for the files in this repository. Case cards on effectsize.io summarize other people's work; originals are linked.
