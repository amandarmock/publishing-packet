# Step three: connect an SEO MCP

An MCP (Model Context Protocol) server is a way to hand Claude Code a new set of tools. This one
gives it YouTube-native search volume and competition numbers for phrases. With it connected,
step 3 of `/find-ideas` can prefer phrases people actually type into YouTube instead of phrases
that merely sound right. Without it, the skill falls back to web search. Without that, it works
from `input/keywords.md` alone. Every tier produces a full result; the MCP just makes it sharper.

## The primary option: vidIQ MCP

vidIQ runs an official, remote MCP server. You log in through the browser. There is no API key
to copy around.

1. Have a vidIQ account. As of August 2026 a free account works during their launch period.
   Most tool calls cost 5 credits. Check support.vidiq.com for the current plan rules before
   you rely on it.

2. In the project folder, register the server:

   ```
   claude mcp add --transport http vidiq https://mcp.vidiq.com/mcp
   ```

3. Start Claude Code, run `/mcp`, pick the vidiq server, and choose Authenticate. A browser
   window opens. Log in to vidIQ and approve the connection.

4. Run `/mcp` again. You should now see the server's tool list. Tool names only appear after
   login, so do not hard-code them into a skill or script. The `find-ideas` skill asks for
   "its keyword research tool" and lets Claude find it by description.

5. Run `/find-ideas` on a topic again. The "Search used" line at the top of the new ideas file
   should say `vidIQ MCP`.

### Sharing the setup with a team

By default `claude mcp add` stores the server in your personal config. Add `--scope project`
and it writes a `.mcp.json` file in the repo root instead, so anyone who clones the repo gets
the same contact list:

```json
{"mcpServers":{"vidiq":{"type":"http","url":"https://mcp.vidiq.com/mcp"}}}
```

That file does not log anyone in. It only says where the server lives. Each person still runs
`/mcp` and authenticates with their own vidIQ account.

## The fallback: a YouTube Data API MCP

If vidIQ is not an option, `@kirbah/mcp-youtube` is free and MIT licensed. It needs a YouTube
Data API key, which you create in Google Cloud. It gives a different signal: what currently
ranks for a query and how many views those videos have. That is not search volume, but it is
real data about what the platform rewards.

```
claude mcp add youtube --env YOUTUBE_API_KEY=YOUR_KEY -- npx -y @kirbah/mcp-youtube
```

Then follow steps 4 and 5 above. The "Search used" line will name whichever source Claude found.

## If it breaks

If the MCP hiccups live, the process still runs; that is by design.
