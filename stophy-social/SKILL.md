---
name: stophy-social
description: |
  Get posts, profiles, and threads from Reddit, Instagram, X, Threads, Bluesky, Mastodon, Telegram, LinkedIn, Pinterest, Tumblr, Snapchat, and Quora. Use for "search Reddit for", "what does this profile post about", "read this thread's replies", "what's this company posting on LinkedIn", "find pins about", "read this Quora answer". For YouTube, TikTok, or Kick video content use stophy-video. For ad libraries use stophy-ads. For job posts on LinkedIn use stophy-jobs.
metadata:
  author: stophy
  version: "3.0.0"
allowed-tools:
  - Bash(stophy *)
  - Bash(npx -y @stophy/cli *)
---

# stophy social

Search and read posts, profiles, and threads across a dozen social platforms.

**Prerequisite:** every command here needs `stophy login --browser` or `STOPHY_API_KEY`. See the stophy skill for setup.

## Quick start
```bash
# search a subreddit or all of Reddit
stophy reddit search "bun vs node" --sort top --within month -o .stophy/reddit.md

# a profile's bio, stats, and recent posts
stophy instagram profile natgeo -o .stophy/profile.md

# a single post's text and stats
stophy x tweet "https://x.com/jack/status/20" -o .stophy/tweet.md

# a company's LinkedIn posts
stophy linkedin company posts openai --limit 10 -o .stophy/li-posts.md

# search pins on a topic
stophy pinterest search "kitchen ideas" --limit 25 -o .stophy/pins.md

# a question and its answers
stophy quora question "https://www.quora.com/What-is-the-best-way-to-learn-programming" -o .stophy/quora.md
```
Run `stophy <source> --help` (reddit, instagram, x, threads, bluesky, mastodon, telegram, linkedin, pinterest, tumblr, snapchat, quora) for every command, and `stophy <source> <command> --help` for all options.

**Done when:** you quoted the posts or replies that answer the question, with a link back to the profile, post, or thread.

## Tips
- Most platforms share the same shape: `profile`/`search` to find someone or something, then `posts` for their feed, then `post` for one item's full thread and replies.
- `linkedin posts --profile <p>` or `--company <c>` covers both people and companies; `linkedin company posts <company>` is the shortcut for just a company.
- Page long feeds with `--cursor` from the previous result; save anything past a handful of posts with `-o` and read it in parts instead of flooding chat.

## See also
- [stophy](../stophy/SKILL.md): setup, errors, and reporting a problem
- [stophy-video](../stophy-video/SKILL.md): YouTube, TikTok, and Kick
- [stophy-jobs](../stophy-jobs/SKILL.md): LinkedIn job search, separate from LinkedIn posts and profiles
- [stophy-ads](../stophy-ads/SKILL.md): ad libraries for Meta, LinkedIn, Pinterest, Snapchat, and more
