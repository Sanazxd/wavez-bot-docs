# Changelog

🇨🇿 [Česky](../cs/changelog.md) · [← Back](README.md)

This bot is a fork of **[fluteds/wavez-bot](https://github.com/fluteds/wavez-bot)** by fluteds. The fork starts from the original's latest commit, `f16e723` (2026-09-26, version 1.1.0); everything below came after it.

## Compared with the original

| | Original 1.1.0 | This fork 2.0.5 |
| --- | --- | --- |
| Languages | English only | English and Czech, switched in chat with `!en` / `!cz` |
| Commands | 40 | 26: adds `!ruleta`/`!join`, `!clear`, `!en`, `!cz`; drops `!vibe`, `!theme`, `!rules`, `!dupe`, `!top`, the custom replies (`!addcmd`, `!delcmd`) and the booth, queue, vote and history commands (`!nowplaying`, `!score`, `!queue`, …) |
| `!help` | every command in one list | categories with counts; `!help <category>` and `!help <command>`; only what you can use; links to these docs |
| Role ladder | `user < resident_dj < bouncer < manager < cohost < host` | adds `vip` between `user` and `resident_dj` |
| Platform titles | `admin` counts as manager, `ambassador` as bouncer | only `admin` counts as manager; ambassadors are whatever the room made them |
| Welcomes | one line, at most once per person every 10 minutes | separate random lines for host, staff, resident DJs and VIPs; every real arrival greeted; farewells |
| Presence | believed every join and leave Wavez reported | tracks who is actually in the room: repeat joins, offline staff, closed tabs, reconnects, connection blips |
| AFK | flag cleared on the next message | welcome back with how long and who asked; replies to @-mentions; notices cleaned up afterwards |
| Room automation | none | auto-skip, emote train, crowd celebration at 10 people, ruleta raffle |
| Chat cleanup | none | command messages deleted, replies deleted after a minute and other bot messages after an hour, `!clear` |
| Reply style | plain lower-case text | one consistent style: leading emoji, ` · ` between items, flags |

## 2.0.5 — 2026-10-30

### Changed

- **Every command cools down for 3 seconds.** Moderation and settings commands, `!ping` and `!ruleta` used to wait 5 seconds and `!clear` 10.

### Removed

- **Custom replies:** `!addcmd` (`!addcommand`, `!learn`) and `!delcmd` (`!delcommand`, `!forget`), and the **Canned** category in `!help`. Replies taught earlier no longer answer.
- **The booth and queue commands:** `!nowplaying` (`!np`, `!song`), `!time` (`!elapsed`, `!left`), `!dj`, `!next` (`!upnext`), `!djs` (`!lineup`, `!booth`), `!queue` (`!q`, `!wait`) and `!position` (`!pos`, `!waittime`).
- **The vote commands:** `!score` (`!rating`) and `!votes` (`!woots`). Auto-skip still reads the votes.
- **`!mods`** (`!staff`).
- **`!history`** (`!last`, `!recent`). The bot no longer keeps a list of the last 20 tracks; `!seen` still knows what each person last played.

### Fixed

- **The `!ruleta` announcement** tagged or replied to the manager who opened the round when the room's reply mode was set to mention or reply. It now goes to `@everyone` only.

## 2.0.4 — 2026-10-30

### Changed

- **`!ping` shows the round trip** to the server in milliseconds (`🏓 Pong · 42 ms`), or says the server did not answer.
- **Emote train bursts stay in chat** instead of being deleted after an hour.

### Removed

- **`!rules`** (`!etiquette`). The bare `!help` still links to this documentation.
- **`!dupe`** (`!again`, `!heardit`).
- **`!top`** (`!best`).

### Fixed

- **`!move`** put people one spot lower than asked, and `!move <user> 1` did nothing. It now moves them to the spot typed, says so if they are not in the queue, and says it moved them only once the server has done it.

## 2.0.3 — 2026-10-30

### Changed

- **`!rules` links to this documentation** instead of printing rules from the bot's settings. It says the rules and documentation are on GitHub, with the link.
- **AFK notices start with `:brb:`** instead of 💤: the away notice and the replies to @-mentions.
- **The startup line is deleted after a minute** instead of an hour.

### Removed

- **`!theme`** (`!genre`).
- **`!ruleta leave` and `!ruleta list`**, and `!ruleta join` with them. `!join` is the only way into a round, and an entry stays in until the draw.

## 2.0.2 — 2026-10-28

### Changed

- **Only managers open the ruleta.** A bare `!ruleta` now needs a manager, not a bouncer. Joining with `!join`, `!ruleta leave` and `!ruleta list` stay open to everyone.
- **The crowd celebration tags nobody.** The cheer at 10 people is for the whole room, so it no longer @-mentions the person whose arrival tipped it.

## 2.0.1 — 2026-10-16

### Changed

- **Replies to commands** are deleted after a minute instead of an hour, canned replies included. The `!afk` notice still stays until the person is back, and welcomes, farewells and ruleta announcements still stay an hour.
- **Ambassadors no longer count as bouncers.** They are whatever role the room gave them. `admin` still counts as manager.

### Fixed

- **Connection blips** no longer cause a farewell and a new welcome. A farewell comes only on a real leave, a leave in Wavez's own log, or after a minute out of the room.
- **Ambassadors who are plain users in the room** were greeted as staff and could run manager commands, because Wavez reports them as managers. The bot now goes by the role the room assigned.
- **`!users`** counted the bot in the headcount and listed people as AFK after they had left. It now counts only people in the room and lists only their AFK.
- **Leaving the room ends AFK**, quietly, with no welcome back on return. AFK left over from people who left while the bot was offline is cleared at startup.

## 2.0.0 — 2026-10-14

### Added

- **Ruleta raffle.** A bouncer opens a round with `!ruleta` and everyone gets an `@everyone` announcement. People enter with `!join` within a minute, and the bot draws a winner and moves them to #1 in the queue, adding them to it first if needed. The announcement says where the winner came from. If the draw lands on the DJ who is playing, it draws again.
- **Czech.** Every line the bot says exists in English and Czech. Managers switch with `!en` / `!cz`, and the choice is saved. Czech lines about a person are worded gender-neutrally.
- **Per-role welcomes.** The host, staff, resident DJs and VIPs each have their own list of greetings, picked at random and never the same twice in a row, with an hour before a special greeting repeats. Welcomes @-mention the person.
- **Farewells.** The bot says goodbye when someone leaves and takes it down after an hour or when they come back. Only the latest welcome or farewell per person stays in chat.
- **Presence tracking.** The bot greets only real arrivals and notices people who close the tab or drop out, including between two room lists. It checks who is in the room every 30 seconds.
- **AFK overhaul.**
  - The welcome back says how long you were away and who asked for you, and disappears after 15 seconds.
  - @-mentioning someone who is AFK gets a reply with how long and why, once per person every 5 minutes.
  - `!afk` alone ends AFK and `!afk <reason>` changes the reason.
  - The away notice and the mention replies come down once the person is back.
- **Auto-skip.** A track is skipped once mehs are at least half of all votes, never in its first 30 seconds.
- **Emote train.** When 3 people post `:kong:` within 2 minutes, the bot joins in with 5–15 of them.
- **Crowd celebration.** The bot says something when the room reaches 10 people.
- **Chat cleanup.**
  - Command messages are deleted after they are answered.
  - The bot's own messages are deleted after an hour, and `!help` replies after a minute.
  - `!clear` lets a bouncer delete the bot's messages.
- **VIP role** on the ladder, with its own welcome and no moderation powers.
- **`!help` by category**, with `!help <category>` (English or Czech name) and a link to this documentation.
- **Bilingual documentation**: this site.

### Changed

- **One reply style** for every command: a leading emoji, sentence case, ` · ` between items, `Title — Artist` for tracks.
- **`!score`** draws a bar (`▰▰▰▰▰▰▰▱▱▱ 72%`).
- **`!mods`** groups staff by role.
- **`!user`** shows a country flag.
- **`!nowplaying`** shows time left as `2:41`.
- **Long replies** are split between items rather than mid-sentence, and numbered `(1/3)`.

### Removed

- **`!vibe`** (`!mood`).
- **The 10-minute limit on welcomes.** Each new welcome replaces the previous one instead, so reconnects no longer spam the chat.

### Fixed

- **Welcomes** go only to people actually arriving, not to repeat joins or offline staff, and someone reconnecting after closing the tab is welcomed again.
- **Farewells** are said for people who drop out without leaving properly (closed tab, lost connection).
- **AFK mentions** are detected from the message text, and the bot never tags itself in AFK notices.
- **`!join` cannot be spammed**, and is ignored when no round is open.
- **The ruleta winner** is moved to position 1 correctly (the queue position is one-based).
- **The crowd celebration** fires when the room reaches exactly 10.

## 1.1.0 and earlier

See the [original repository](https://github.com/fluteds/wavez-bot/commits/main) for the history before the fork:

- initial release: chat and moderation bot
- `Accept-Language` so server errors are not in Portuguese
- splitting replies over the message limit
- @mention replies
- unknown roles get no powers
