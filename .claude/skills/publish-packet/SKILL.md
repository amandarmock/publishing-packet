---
name: publish-packet
description: Turns a piece of content (video transcript, blog post, newsletter draft, or one idea from an ideas/ file) into a publishing packet with ranked title options, description, chapters or outline, hashtags, tags, and thumbnail text. Use when the user asks to package, title, or prepare content for publishing, or runs /publish-packet.
---

# Publish Packet

Follow the process in CLAUDE.md and every rule in .claude/rules/,
especially seo-reality.md.

## Steps

1. Identify the source. It is one of two kinds:
   - Finished content: a file in input/transcript/. If the user didn't
     name one, use the most recent file there and confirm which one.
   - An idea: the user names an ideas/ file and a rank number (for
     example "/publish-packet ideas/ideas-2026-08-20-claude-code.md #1").
     The source is that one row. Say which kind you are working from.
2. Read the source content, input/channel-context.md, input/keywords.md,
   and input/reference-titles.md.
3. Pull out the core promise: what does someone walk away with? One
   sentence. For finished content, take it from what was actually said.
   For an idea, take it from the idea's promise column. Everything else
   hangs off this.
4. Generate 8 title options. Vary the angle: some clarity-first for
   search, some curiosity-first for browse. For each, note the character
   count and which keyword from keywords.md it carries. A title carries
   a keyword only if that phrase appears in the title text (ignore
   differences in capitalization and hyphenation). Every title should
   carry at least one keyword. Follow
   the title guidance in seo-reality.md.
5. Ask the title-critic agent to score and rank all 8. Present the top 5
   in ranked order with the critic's one-line reasoning for each.
   Use the Agent tool with subagent_type "title-critic" and pass it the
   8 titles, the source path, and the channel-context path. If the
   source is an idea, tell the critic so: promise match then means
   "could this channel honestly deliver this", not "does the transcript
   deliver this".
6. Draft the description: first two sentences carry the main keyword and
   the core promise, then a short scannable summary, then 3 questions
   this content answers, phrased the way someone would search them.
7. Chapters or outline. For finished content with timestamps, build
   chapters: group into 8 to 15, one per topic shift, not one per
   timestamp, each starting at a timestamp that exists in the source.
   For content without timestamps, or for an idea, write a proposed
   outline of 6 to 10 sections instead, and title the section
   "Proposed outline". Descriptive titles either way, each one a phrase
   someone might search.
8. Generate 3 to 5 hashtags, and 8 to 12 tags per the insurance-only
   policy in seo-reality.md.
9. Suggest 2 to 3 thumbnail text ideas (5 words or fewer each) that pair
   with the #1 ranked title without repeating it word for word.
10. Before saving, count and check every hard number in this skill:
    8 titles generated, 5 ranked, character counts exact, 8 to 15
    chapters or 6 to 10 outline sections, 3 to 5 hashtags, 8 to 12
    tags, each thumbnail idea 5
    words or fewer. Fix anything that misses. Do not write counts or
    check notes into the packet itself. Then save the complete
    packet to output/ using the naming convention in CLAUDE.md, and
    show the ranked titles in the conversation.

## Output format for the packet file

# Publishing Packet: [content name]
Generated: [date]
Source: [path, and "idea #N" if it came from an ideas file]

## Titles (ranked)
| Rank | Title | Chars | Keyword | Why |

## Description
[draft]

## Chapters  (or "## Proposed outline" when there are no timestamps)
[timestamp list or numbered outline]

## Hashtags
## Tags (insurance layer only, see seo-reality.md)
## Thumbnail text ideas
