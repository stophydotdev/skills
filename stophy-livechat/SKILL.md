---
name: stophy-livechat
description: Read YouTube live stream chat and status with Stophy CLI. Trigger when the user provides a live (or upcoming/replay) video URL and wants live chat messages, super chats, viewer reactions during a stream, concurrent viewer count, or wants to poll a live stream for new chat messages.
metadata:
  author: stophy
  version: "1.0.0"
allowed-tools:
  - Bash(stophy *)
  - Bash(npx @stophy/cli *)
---

# stophy-livechat

Read live chat messages and stream status for a YouTube live stream.

## Choose this skill when

- The user gives a live, upcoming, or replay video URL and wants the chat messages.
- The user wants super chats, moderator/owner messages, or reactions during a stream.
- The user wants the live status, concurrent viewer count, or to follow a stream for new messages.

Use `stophy-comments` for regular (non-live) video comments. Use `stophy-transcript` for spoken content.

## Commands

```bash
# Live chat + stream status (Top chat, moderated, default)
stophy video livechat --url "https://www.youtube.com/watch?v=h6ukrWyqOm4"

# All messages (Live chat) instead of moderated Top chat
stophy video livechat --url "https://www.youtube.com/watch?v=h6ukrWyqOm4" --chatType live

# Poll for only new messages using the previous response's continuation token
stophy video livechat --url "https://www.youtube.com/watch?v=h6ukrWyqOm4" --continuation-token <token>
```

## Options

| Option | Values | Use when |
|--------|--------|----------|
| `--url <url>` | YouTube video URL | Always required |
| `--chatType <type>` | top, live | `top` = moderated Top chat (default); `live` = all messages. Applied on the first call; later polls keep the chosen mode |
| `--continuation-token <token>` | string | Poll for new messages from a previous livechat response |
| `--json` | — | Pipe or parse raw JSON |

## Response shape

`livechat` returns fields such as:

- `status` — one of `live`, `upcoming`, `replay`, `chat_disabled`, `not_live`
- `isLive`
- `concurrentViewers`
- `messages[]` — each with `text`, `author`, `authorId`, `timestampUsec`, `isOwner`, `isModerator`, `isVerified`, `superChatAmount`
- `continuationToken`
- `pollIntervalMs`

## Output guidance

- To follow a live stream, call again passing the previous `continuationToken` to get only new messages, waiting `pollIntervalMs` between polls.
- A `null` `continuationToken` means the stream ended — stop polling.
- Highlight super chats (`superChatAmount`) and owner/moderator messages when summarizing.
- If `status` is not `live`, tell the user the stream isn't live rather than implying real-time data.

## Related skills

- [stophy-comments](../stophy-comments/SKILL.md) — read regular video comments and replies
- [stophy-video](../stophy-video/SKILL.md) — get video metadata
- [stophy-transcript](../stophy-transcript/SKILL.md) — get spoken content
- [stophy-search](../stophy-search/SKILL.md) — find videos before reading chat
