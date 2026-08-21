# Publishing Packet

This project takes a topic, finds content ideas for it, and turns a
piece of content (a video transcript, a blog post, a newsletter draft,
or one of those ideas) into a "publishing packet": everything needed to
package and publish it well.

## Folder map
- input/transcript/ : the source content goes here
- input/channel-context.md : who we're talking to and how we sound
- input/keywords.md : validated search phrases (offline fallback)
- input/reference-titles.md : packaging examples from the niche
- input/content-backlog.md : what's already planned, so ideas don't repeat it
- ideas/ : ranked idea lists land here, one file per topic
- output/ : finished packets land here, one file per piece of content

## How we work
Two steps, each its own skill. Step one finds ideas. Step two packages
one piece of content, which can be a finished transcript or one idea
from step one.

1. Read channel-context.md before doing anything else
2. /find-ideas takes a topic and writes a ranked idea list to ideas/
   named ideas-YYYY-MM-DD-short-topic-slug.md
3. /publish-packet takes a source (a transcript, or one idea) and writes
   a packet to output/ named packet-YYYY-MM-DD-short-slug.md
4. A packet contains, in this order: ranked title options, description,
   chapters (or a proposed outline), hashtags, tags, thumbnail text ideas
5. Never publish, post, or send anything. This project prepares; a human publishes.
