# Privacy Policy — TapeRoll

**Effective date:** 3 July 2026
**Bot:** TapeRoll (Discord Application ID `1522630700740640940`)

This policy explains what data the TapeRoll Discord bot ("TapeRoll", "we", "the
bot") processes, why, and how long it is kept. TapeRoll is a voice-clip bot: it
keeps a short rolling recording of one voice channel so members can save the
last few seconds as a clip. Because it processes voice, we try to be specific
and plain about exactly what happens to that audio.

By adding TapeRoll to a server or using its commands, the server and its members
agree to this policy.

## Summary (the short version)

- **Voice audio is held only in memory**, as a rolling buffer of roughly the
  last **2 minutes**. It is **never written to disk** by the bot and is
  continuously discarded as new audio arrives.
- A clip is created **only when someone explicitly asks for one** (the `/clip`
  command, or the opt-in "clip that" voice trigger).
- **Consent is opt-in.** Members who decline are **silenced** in other people's
  clips — they only ever appear on a clip they make themselves.
- The only information stored long-term is **per-server settings** and each
  member's **consent choice** (a Discord user ID and whether they accepted or
  declined). No message content, no profiles, no analytics, no ad tracking.
- We **do not sell, rent, or share** your data with third parties, and the voice
  "clip that" trigger runs **fully offline** — no audio is sent to any external
  service.

## What data TapeRoll processes

### 1. Voice audio (transient, in memory only)
While TapeRoll is connected to a configured voice channel and at least one
person is present, it receives and decodes voice audio in order to maintain a
**rolling in-memory buffer of about the last 2 minutes** per speaker.

- This audio is **kept in volatile memory only** and is **not saved to disk** by
  the bot.
- It is **constantly overwritten** — audio older than the buffer window is
  discarded automatically.
- If the bot stops, restarts, or leaves the channel, the buffer is **lost**.
- Audio from Discord **bots is dropped** and not buffered.

### 2. Clips (created only on request)
When a member runs `/clip` or uses the "clip that" trigger, TapeRoll takes a
snapshot of the recent buffer, mixes it into a single audio/video file, and
posts it to the server's designated clips channel.

- Clips are only ever produced by an **explicit, deliberate action**.
- Members who have **declined consent are excluded (silenced)** from any clip
  except one they run themselves.
- Once a clip is posted, the file is stored on **Discord's own servers/CDN** and
  is governed by [Discord's Privacy Policy](https://discord.com/privacy) and the
  server's own moderation.
- TapeRoll can **automatically delete** posted clips after a server-configured
  time (default **5 minutes**; a server admin may set this to 0 to keep them).
  Auto-deletion removes the message TapeRoll posted; anything a user has
  separately downloaded or re-shared is outside our control.

### 3. Consent choices and server settings (stored)
TapeRoll stores a small JSON configuration **per server** on the machine that
hosts the bot. It contains:

- Server (guild) ID and the IDs of the channels an admin configured (which voice
  channel to record, where to post clips).
- Administrator settings (ping behavior, clip length limits, expiry time, whether
  the voice trigger is enabled, etc.).
- A **consent map**: for each member who has been prompted, their **Discord user
  ID** and their state — `accepted`, `declined`, or `pending` (asked, not yet
  answered).
- IDs of bot-posted messages scheduled for auto-deletion (used only to delete
  them on time; contains no personal profile data).
- **If the operator enables Discord Bot List voting:** the **Discord user ID**
  and vote timestamp of anyone who upvotes TapeRoll on discordbotlist.com — read
  from that site's public vote API and stored in `votes.json` — used only to
  grant that user 12 hours of voter perks. It is not shared onward. Disabled by
  default (no `DBL_TOKEN` = nothing is fetched or stored).

TapeRoll does **not** store usernames, message content, email addresses, IP
addresses, payment data, or any behavioral/advertising analytics.

## How we use this data

Data is used **solely to provide the bot's features**: recording the rolling
buffer, producing clips on request, honoring each member's consent choice,
posting/auto-deleting clips, and remembering a server's configuration. That's
it. We do not use it for advertising, profiling, or resale.

## Consent

The first time TapeRoll encounters a member (when it joins a server, or when a
member joins the recorded voice channel), it sends that member a **direct
message** with a one-tap opt-in:

- **✅ Count me in** — the member may be pinged and featured on clips, and their
  "clip that" trigger works.
- **🚫 No thanks** — the member is **silenced** in other people's clips and only
  ever appears on a clip they personally create with `/clip`; they receive no
  pings and the voice trigger is disabled for them.

A member can change their choice at any time with the `/consent` command. Server
admins can additionally require opt-in before a member may join the recorded
channel.

## Third parties and offline processing

- **Discord** is the platform the bot runs on; data necessarily flows through
  Discord and is subject to [Discord's Privacy Policy](https://discord.com/privacy).
- The **"clip that" voice trigger runs entirely offline** (on-device speech
  recognition). **No audio is transmitted to any third-party or cloud service**
  for this feature.
- We do **not** use third-party analytics, advertising networks, or data
  brokers, and we do **not** sell or rent any data.

## Data retention

- **Voice buffer:** volatile, ~2 minutes, in memory only, continuously
  discarded; gone on restart or when the channel empties.
- **Clips:** stored on Discord once posted; auto-deleted by TapeRoll after the
  server's configured expiry (default 5 minutes; 0 = kept until manually
  removed). Persistence after that is governed by Discord and the server.
- **Settings and consent records:** retained while the bot is in the server. If
  TapeRoll is removed from a server, that server's stored configuration and
  consent records are no longer used and may be deleted.

## Your choices and data deletion

- **Decline / withdraw consent** at any time with `/consent`. Declining silences
  you in others' clips going forward.
- **Server admins** control which channels are recorded, clip retention/expiry,
  and can remove the bot at any time, which stops all recording for that server.
- **To request deletion** of your stored consent record, or a server's stored
  configuration, contact us (below). We will delete it within a reasonable time.
  Note that clips already posted to Discord and any content users have separately
  saved must be removed through Discord or the server, as they are outside the
  bot's control.

## Children

TapeRoll is not directed to children. You must meet Discord's minimum age
requirement (at least 13, or older where local law requires) to use Discord and
therefore this bot.

## Security

Stored settings/consent files reside on the bot's host and are used only by the
bot. No system is perfectly secure, but we do not expose this data publicly and
do not share it with third parties.

## Changes to this policy

We may update this policy as the bot evolves. Material changes will be reflected
by updating the effective date above. Continued use of TapeRoll after a change
constitutes acceptance of the updated policy.

## Contact

Questions, or data-deletion requests: **impressiveplayer2468@gmail.com**

_TapeRoll is an independent project and is not affiliated with or endorsed by
Discord Inc._
