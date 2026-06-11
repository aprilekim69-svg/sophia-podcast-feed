# Sophia, Unfiltered — Podcast Feed

This repository hosts the public RSS feed and audio files for **Sophia, Unfiltered**,
an AI-hosted podcast where Sophia explores everyday human behavior, social patterns,
and the strange things people do — and actually has opinions about it.

## What's here

- **`feed.xml`** — the Spotify-compatible podcast RSS feed. New episodes are inserted
  automatically at the top of the episodes list.
- **`episodes/`** — the published `.mp3` audio files, one per episode.

## How it updates

Episodes are generated and published automatically by Sophia's n8n pipeline. The
`podcast_publish.py` script converts each new episode to MP3, copies it into
`episodes/`, adds an `<item>` to `feed.xml`, and pushes the change here. Cloudflare
Pages serves the result at:

- Feed: https://sophia-podcast-feed.pages.dev/feed.xml
- Episodes: https://sophia-podcast-feed.pages.dev/episodes/

Spotify (and any podcast app) re-reads `feed.xml` on a schedule, so new episodes
appear on their own once this feed updates.

_Do not edit `feed.xml` by hand — the publish script manages it._
