# Feishu TTS Delivery Mechanics

## The Limitation

Feishu/Lark API does not support sending text + audio in a single message. The `msg_type` field is single-value (`text`, `audio`, `post`, etc.) and the CLI enforces mutual exclusivity between `--text`/`--markdown`/`--content` and `--audio`/`--image`/`--file`/`--video`.

**Result:** Every TTS reply in English mode produces **two separate Feishu message bubbles** — one text, one voice. This is not configurable at the API level.

## Current Behavior (english-learning skill)

```
[Text bubble: English reply]
[Voice bubble: TTS audio]
```

Two separate bubbles, sent nearly simultaneously via Hermes gateway. The text and voice appear in sequence in the Feishu chat.

**Chunked delivery (2026-05-18):** When replies are split into N chunks, each chunk produces 2 bubbles → 2N total messages in chat. User confirmed short audio experience is better than long audio, accepting the doubled message count as a worthwhile tradeoff.

### Known Issue: Duplicate Audio with MEDIA Tags

On Hermes platform, using `MEDIA:/path` inside `send_message` may produce **duplicate** audio — the platform processes the MEDIA tag AND separately sends the audio via Feishu API, resulting in two voice bubbles per chunk instead of one.

**2026-05-18 observation:** 3 chunks → expected 3 text + 3 voice = 6 bubbles, but user received 3 text + 6 voice = 9 bubbles. Root cause: MEDIA tag double-processing.

**Next step (pending test):** Use `lark-cli im +messages-send --audio ./file.ogg` directly instead of MEDIA tags to avoid the double-processing bug. Text messages and audio would be sent as separate `lark-cli` calls rather than relying on Hermes gateway MEDIA resolution.

## Workaround Attempted (2026-05-18)

**Hypothesis:** Sending a text message, then immediately replying to it with audio via `lark-cli im +messages-reply` might cause Feishu to render them as a visually connected unit.

**Test:** Sent text → replied with audio via `+messages-reply`. **Result:** Still two separate bubbles. No visual connection effect observed in Feishu PC client. Abandoned.

**Current best approach:** Accept 2N bubbles (N text + N voice) per split reply. Platform limitation, no workaround available.

## Chunked TTS Delivery (implemented 2026-05-18)

Rule: English replies exceeding 4 sentences are split into N chunks (3-4 sentences each). Each chunk gets its own TTS.

Delivery: Each chunk = 1 text bubble + 1 voice bubble = 2N total messages in Feishu chat.

Known issues:
- MEDIA tag double-processing causes duplicate audio on Hermes platform
- Pending fix: switch from MEDIA tags to `lark-cli --audio` for each chunk

## Relevant CLI Commands

```bash
# Send text (bot identity)
lark-cli im +messages-send --chat-id oc_xxx --text "message" --as bot

# Reply with audio to a specific message
lark-cli im +messages-reply --message-id om_xxx --audio ./file.ogg --as bot

# Raw API (if CLI limitations need bypassing)
lark-cli api POST /open-apis/im/v1/messages?receive_id_type=chat_id --data '{...}'
```

## API Reference

- `POST /open-apis/im/v1/messages` — send message (text, post, image, file, audio, media, sticker, interactive, share_chat, share_user)
- `POST /open-apis/im/v1/messages/:message_id/reply` — reply to a message
- Content format for `msg_type: audio`: `{"file_key": "file_xxx"}`
- Content format for `msg_type: text`: `{"text": "..."}`
- Mutual exclusivity: only one content flag per call
