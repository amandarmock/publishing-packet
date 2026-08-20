# Publishing Packet

This project turns a finished piece of content into a publishing packet: ranked title options, a description, chapters, hashtags, tags, and thumbnail text ideas. A separate critic agent scores the titles against the transcript so the one that wins is the one the content can actually back up. You drop a transcript in, run one command, and get a single markdown file ready for a human to copy from.

## Who this is for

This is the companion repo for the Claude Code Masterclass for Beginners by Purpose Built. Clone it and build along with the video. You do not need to be a developer. If you can edit a text file and type a command, you can follow every step.

## Quick start

```
git clone https://github.com/amandarmock/publishing-packet.git
cd publishing-packet
claude
```

Then, inside Claude Code, type:

```
/publish-packet
```

Open the file that lands in `output/` and read the packet.

## What's in the box

```
publishing-packet/
├── README.md
├── CLAUDE.md                         folder map preloaded, process built on camera
├── input/
│   ├── transcript/
│   │   └── sample-video.md           preloaded sample
│   ├── channel-context.md            preloaded
│   ├── keywords.md                   preloaded, offline fallback
│   └── reference-titles.md           preloaded
├── output/
│   └── .gitkeep
└── .claude/
    ├── settings.json                 starter preloaded
    ├── rules/
    │   ├── seo-reality.md            preloaded
    │   └── transcripts-are-sacred.md built on camera
    ├── skills/
    │   └── publish-packet/
    │       └── SKILL.md              frontmatter preloaded, body built on camera
    └── agents/
        └── title-critic.md           built on camera
```

## What's preloaded and what you build in the video

| Preloaded | Built on camera |
| --- | --- |
| Sample inputs in `input/` | CLAUDE.md "How we make a packet" section |
| `seo-reality.md` rule | `transcripts-are-sacred.md` scoped rule |
| `settings.json` starter | `publish-packet` skill body |
| Skill frontmatter | `title-critic` agent |
| CLAUDE.md folder map | |

If you get lost, the `complete` branch has the finished version of every file.

## A note on tags

YouTube's own help documentation says tags play a minimal role in discovery. Most tutorials skip past that. This repo says it out loud, generates a small set of tags as insurance for misspellings and brand variants, and spends its effort on the things that matter: title, thumbnail, description, and chapters.

## Not just for YouTube

The worked example is a video transcript, but the process does not care what the content is. Swap the transcript for a newsletter draft, a product listing, or a blog post and run the same command. You get the same packet format with no re-explaining.

## Guardrails

Claude can read `input/` and `.claude/`, and can write only to `output/`. It is denied from editing anything in `input/` and from running `rm`. Nothing in this project publishes, posts, or sends anything. This project prepares; a human publishes.
