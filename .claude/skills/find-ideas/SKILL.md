---
name: find-ideas
description: Generates a ranked list of content ideas for a topic, grounded in the channel's audience, validated keywords, and existing backlog. Use when the user asks for video ideas, content ideas, what to make next, or runs /find-ideas. Output feeds /publish-packet.
---

# Find Ideas

Follow the process in CLAUDE.md and every rule in .claude/rules/,
especially seo-reality.md.

## Steps

1. Identify the topic. If the user gave one with the command, use it. If
   not, ask for one in a single sentence and stop until you have it.
2. Read input/channel-context.md, input/keywords.md,
   input/reference-titles.md, and input/content-backlog.md.
3. Get search signal, best available first:
   - If an SEO MCP is connected (vidIQ, for example), use its keyword
     research tool on the topic and on your candidate phrases. Prefer
     phrases with real YouTube search volume and workable competition.
   - Otherwise, if web search is available, run 2 or 3 searches for what
     people are asking about this topic right now.
   - Otherwise, work from keywords.md alone.
   Record which tier you used on the "Search used" line. Note any
   phrases worth adding to keywords.md. The process must produce a full
   result at every tier.
4. Generate 10 ideas. Each idea is one thing a viewer walks away with,
   not a category. Vary the shape: some how-to, some explainer, some
   build-along, some comparison. Skip anything already on the backlog,
   but feel free to propose a follow-on that hangs off a backlog item
   and name which one.
5. For each idea write: a working title, the one-sentence promise, the
   primary search phrase it targets (from keywords.md or a search), the
   format (how-to, explainer, build-along, comparison), and a difficulty
   note for the channel's audience (beginner, intermediate). The working
   title must contain its search phrase as written (ignore capitalization
   and hyphens), starting inside the first 40 characters. If a title
   doesn't, rewrite the title, not the phrase. Any phrase you use that is
   not already in keywords.md goes in the "Phrases worth adding" list.
6. Ask the title-critic agent to score the 10 working titles. Use the
   Agent tool with subagent_type "title-critic" and tell it the source
   is an idea list, not a transcript, so promise match means "could this
   channel honestly deliver this" rather than "does the transcript
   deliver this". Pass it the ideas file content and the channel-context
   path.
7. Rank the ideas by the critic's totals. Present the top 5 in the
   conversation with the critic's one-line reasoning.
8. Before saving, count: 10 ideas, each with all five fields, none
   duplicating the backlog, every working title containing its search
   phrase inside the first 40 characters, every phrase not in keywords.md
   listed under "Phrases worth adding". Fix anything that misses. Do not
   write counts, check notes, or revision history into the file; the
   critic's note describes the title as it stands.
9. Save to ideas/ named ideas-YYYY-MM-DD-short-topic-slug.md. Check
   ideas/ first: if that name already exists, add -2, -3, and so on.
   Never overwrite or delete an existing ideas file. Tell the user the
   next step is /publish-packet with one of these ideas as the source.

## Output format for the ideas file

# Ideas: [topic]
Generated: [date]
Search used: vidIQ MCP | web search | none (keywords.md only)

## Ranked ideas
| Rank | Working title | Promise | Search phrase | Format | Level | Critic's note |

## Backlog items these build on
[list, or "none"]

## Phrases worth adding to keywords.md
[list, or "none"]
