# Aelo plugin

Ask your AI assistant about your team's sales and support calls, chats and
e-mails analysed in [Aelo](https://aelo.cloud). The assistant searches them,
reads transcripts, brings analyses with quotes and timecodes, summarises a
deal and reports team quality for a period. **It only reads** — nothing is
written to Aelo — and it sees only what you see in Aelo yourself, with your
role and group access, in the organization you chose when you connected.

The plugin is a connection to the Aelo MCP server
(`https://mcp.aelo.cloud/mcp`) plus one skill, `aelo-calls`, that keeps the
assistant to what the tools returned: every claim sourced, quotes and
timecodes copied rather than rebuilt, "not confirmed" instead of a guess,
personal data only when asked for. It runs nothing locally.

## Before you start

- An Aelo account on a paid plan (Starter and above) or during the Pro trial.
  The free Pay-as-you-go plan does not include the connector outside the trial.
- Your organization's owner or an admin first switches on **AI assistants
  connected by your users** in **Settings → Organization → New kinds of
  processing**. Until then the assistant receives nothing.
- Full guide for Claude, ChatGPT, Claude Code and Codex:
  <https://aelo.cloud/en/docs/integrations/ai-assistants>

## Install

Claude Code:

```
/plugin marketplace add grow2ai/agent-plugins
/plugin install aelo@grow2ai
/mcp
```

In `/mcp` pick `aelo` → Authenticate → sign in to Aelo, choose the
organization and allow access.

Codex:

```
codex plugin marketplace add grow2ai/agent-plugins
codex plugin add aelo@grow2ai
codex mcp login aelo
```

## Tools

| Tool               | What it returns                                                                      |
| ------------------ | ------------------------------------------------------------------------------------ |
| `search_records`   | calls, chats and e-mails by period, employee, project, category and quality score   |
| `get_transcript`   | the transcript of one record: text, speakers, start/end in seconds (phone numbers, e-mails and card numbers masked) |
| `get_analysis`     | the latest analysis: quality score, summary, key moments with quotes and timecodes, strengths, improvements, agreements |
| `get_deal_summary` | the deal card as the Aelo app shows it                                               |
| `get_team_quality` | team and per-employee metrics for a period, as the Aelo dashboard computes them      |

## Example prompts

- Find last week's calls with a quality score below 60 and tell me what the three worst have in common.
- Open the transcript of the call with Acme from Monday and quote what the customer said about the price, with timecodes.
- What did the analysis of this call list as improvements for the rep?
- Summarise the state of the Northwind deal and what the rep should do next.
- How did my team's quality change this month compared with the previous period, per employee?

## Disconnect

Aelo → **Settings → Profile** lists the connected assistants; **Revoke**
removes access within about a minute. A connection unused for 30 days expires.

## Privacy Policy

Aelo is operated by Auspex Streamline S.L. (Spain). What Aelo collects, how it
is used and stored, who it is shared with and for how long is described in the
Privacy Policy: <https://aelo.cloud/en/legal/privacy> and, for the
organization's data processed on its behalf, the Data Processing Agreement:
<https://aelo.cloud/en/legal/dpa>. This plugin itself collects and stores
nothing: it holds no data and sends no data anywhere except to
`mcp.aelo.cloud`, the Aelo server you sign in to. The assistant you connect
(Claude, ChatGPT, Codex…) receives what its tool calls return; that provider
is your choice and is not Aelo's sub-processor. Contact:
<privacy@aelo.cloud>; support: <support@aelo.cloud>.

## License

MIT, see [`LICENSE`](LICENSE).
