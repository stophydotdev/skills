---
name: stophy-video
description: |
  Get YouTube, TikTok, and Kick data: search videos, read transcripts, comments, channels, playlists, and past streams or clips. Use for "get the transcript of", "what are people saying in the comments", "find videos about", "latest uploads from this channel", "past streams from this creator", "clips from this streamer". YouTube search and transcripts work without an API key. For posts on Reddit, X, or Instagram use stophy-social. For TikTok ad-library ads use stophy-ads.
metadata:
  author: stophy
  version: "3.0.0"
allowed-tools:
  - Bash(stophy *)
  - Bash(npx -y @stophy/cli *)
---

# stophy video

Search and read YouTube, TikTok, and Kick: videos, transcripts, comments, channels, playlists, streams.

**Prerequisite:** `stophy youtube search` and `stophy youtube transcript` work without an API key. Everything else (video details, comments, channel, playlist, all of TikTok and Kick) needs `stophy login --browser` or `STOPHY_API_KEY`. See the stophy skill for setup.

## Quick start
```bash
# no login needed: find videos on a topic
stophy youtube search "rust tutorial" --limit 10 -o .stophy/search.md

# no login needed: read what a video actually says
stophy youtube transcript dQw4w9WgXcQ -o .stophy/transcript.md

# see what viewers are saying
stophy youtube comments dQw4w9WgXcQ --sort top --limit 50 -o .stophy/comments.md

# a creator's recent uploads or shorts
stophy youtube channel @mkbhd --tab videos --limit 30 -o .stophy/channel.md

# same idea on TikTok
stophy tiktok posts khaby.lame --limit 30 -o .stophy/tiktok-posts.md

# a live streamer's past broadcasts
stophy kick videos xqc --limit 25 -o .stophy/kick-videos.md
```
Run `stophy youtube --help`, `stophy tiktok --help`, or `stophy kick --help` for every command, and `stophy <source> <command> --help` for all options.

**Done when:** you quoted the parts of the transcript, comments, or listing that answer the question, alongside the video or channel URL.

## Tips
- Accept both a bare video ID (`dQw4w9WgXcQ`) and a full URL for `video`/`transcript`/`comments`; either works.
- Search first to get an ID, then call `video`, `transcript`, or `comments` on it; `youtube comments replies` and `tiktok comments replies` need a comment ID from the comments call first.
- Page long results with `--cursor` from the previous call; save transcripts and comment lists with `-o` and read them in parts rather than pasting the whole thing into chat.

## See also
- [stophy](../stophy/SKILL.md): setup, errors, and reporting a problem
- [stophy-social](../stophy-social/SKILL.md): posts on Reddit, X, Instagram, and other platforms
- [stophy-ads](../stophy-ads/SKILL.md): TikTok's ad library
