# Publishing Packet

This project is a two-step process. `/find-ideas <topic>` finds and ranks content ideas for your
channel. `/publish-packet` turns one piece of content (a finished transcript, or one of those ideas)
into a publishing packet: ranked titles, a description, chapters or an outline, hashtags, tags, and
thumbnail text. A read-only critic agent scores every title, so the one that wins is the one the
content can actually back up. You run two commands and get markdown files a human can copy from.

## Who this is for

This is the companion repo for the Claude Code Masterclass for Beginners by Purpose Built
(Amanda Mock). Clone it and build along with the video. Not a developer? Good. It was built for
you. If you can edit a text file and type a command, you can follow every step.

## Quick start

```
git clone https://github.com/amandarmock/publishing-packet.git
cd publishing-packet
claude
```

Accept the trust prompt when Claude Code asks. Then, inside Claude Code:

```
/find-ideas your topic here
```

Open the file it writes to `ideas/`, pick a row, and package it:

```
/publish-packet ideas/<the file it made> #1
```

Or skip the ideas step: drop a transcript in `input/transcript/` and run `/publish-packet` alone.
Either way the packet lands in `output/`.

## What's in the box

```
publishing-packet/
├── README.md
├── CLAUDE.md                         folder map preloaded, "How we work" built on camera
├── input/
│   ├── transcript/
│   │   └── sample-video.md           preloaded sample
│   ├── channel-context.md            preloaded
│   ├── keywords.md                   preloaded, offline fallback
│   ├── reference-titles.md           preloaded
│   └── content-backlog.md            preloaded
├── ideas/                            ranked idea lists land here
├── output/                           finished packets land here
├── docs/
│   └── mcp-upgrade.md                preloaded, step three
└── .claude/
    ├── settings.json                 preloaded
    ├── rules/
    │   ├── seo-reality.md            preloaded
    │   ├── transcripts-are-sacred.md built on camera
    │   └── ideas-are-drafts.md       built on camera
    ├── skills/
    │   ├── find-ideas/
    │   │   └── SKILL.md              frontmatter preloaded, body built on camera
    │   └── publish-packet/
    │       └── SKILL.md              frontmatter preloaded, body built on camera
    └── agents/
        └── title-critic.md           built on camera
```

## Preloaded vs built on camera

| Preloaded | Built on camera |
| --- | --- |
| Everything in `input/` | CLAUDE.md "How we work" section |
| `seo-reality.md` rule | `transcripts-are-sacred.md` scoped rule |
| `settings.json` | `ideas-are-drafts.md` scoped rule |
| Frontmatter for both skills | Body of `find-ideas` skill |
| CLAUDE.md folder map | Body of `publish-packet` skill |
| `docs/mcp-upgrade.md` | `title-critic` agent |
| | Step three: the vidIQ MCP connection |

If you get lost, the `complete` branch has the finished version of every file.

## Step three: add an MCP

Once the two skills work, `docs/mcp-upgrade.md` walks through connecting the vidIQ MCP so
`/find-ideas` can see real YouTube search volume instead of guessing. The process works without
it: `keywords.md` is the offline fallback, web search is the middle tier, and the MCP is the top.

## A note on tags

YouTube's own help documentation says tags play a minimal role in discovery. Most tutorials skip
past that. This repo says it out loud, generates a small set of tags as insurance for misspellings
and brand variants, and spends its effort on the things that matter: title, thumbnail,
description, and chapters.

## Not just for YouTube

The worked example is a video transcript, but the process does not care what the content is.
Swap the transcript for a newsletter draft, a product listing, or a blog post and run the same
command. You get the same packet format with no re-explaining.

## Guardrails

Claude can read `input/`, `ideas/`, and `.claude/`, and can write only to `ideas/` and `output/`.
It is denied from editing anything in `input/` and from running `rm`. Nothing in this project
publishes, posts, or sends anything. This project prepares; a human publishes.
