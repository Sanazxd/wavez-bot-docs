# Commands

🇨🇿 [Česky](../cs/commands.md) · [← Back](README.md)

The prefix is `!` unless the room sets another one. `<angle brackets>` are required, `[square brackets]` optional, and `a | b` means either form.

An alias works exactly like the command name: `!np` is `!nowplaying`.

**Who** is the lowest role that can use the command; see [Roles](roles.md). Commands without a role are open to everyone.

**Cooldowns** are per person. Moderation, custom and settings commands, `!ping` and `!ruleta` wait 5 seconds between uses, `!clear` waits 10, and every other command 3.

**Replies** to commands are deleted after a minute; see [A tidy chat](features.md#a-tidy-chat).

## Info

| Command | Aliases | What it does |
| --- | --- | --- |
| `!help [category\|command]` | `commands` | With nothing after it, the categories you can use with a count each, and a link to this documentation. `!help fun` lists a category, `!help np` explains a command. Categories also work by their Czech names (`!help zábava`) |
| `!nowplaying` | `np`, `song` | Title, artist, and time left, e.g. `🎵 Blue Veins — Ash Walker · 2:41 left` |
| `!time` | `elapsed`, `left` | How far into the track we are, as `1:23 / 4:56` |
| `!score` | `rating` | Woots as a percentage, a bar and a verdict, e.g. `📊 ▰▰▰▰▰▰▰▱▱▱ 72% · 18/25 · going down well` |
| `!votes` | `woots` | Woot, grab and meh counts |
| `!dj` | | Who is playing |
| `!next` | `upnext` | The next three in the queue |
| `!djs` | `lineup`, `booth` | The whole queue in order, first eight |
| `!queue` | `q`, `wait` | Queue length, whether it is locked, who is playing |
| `!position [user]` | `pos`, `waittime` | Queue spot and estimated wait; yours unless you name someone. Quote names with spaces: `!position "Slow Poke"` |
| `!users` | `active`, `pop` | How many people are in the room (the bot not counted), and which of them are AFK |
| `!user <name>` | `whois`, `profile` | Someone's Wavez profile: platform title, level, fans, country flag |
| `!mods` | `staff` | Staff the bot has seen recently, grouped by role |
| `!seen <user>` | `lastseen` | When someone last spoke and what they last played |
| `!history [count]` | `last`, `recent` | The last few finished tracks, newest first, up to five |
| `!dupe` | `again`, `heardit` | Whether the current track was among the last 20, and who played it |
| `!top` | `best` | The best received of the last 20 tracks (woots minus mehs) |
| `!rules` | `etiquette` | The room rules |
| `!theme` | `genre` | Tonight's theme, if there is one |
| `!afk [reason]` | `away`, `brb` | Mark yourself away. See [AFK](features.md#afk) |
| `!uptime` | | How long the bot has been running |
| `!ping` | `pong` | Checks the bot is alive |

## Fun

| Command | Aliases | What it does |
| --- | --- | --- |
| `!8ball <question>` | `eightball` | Ask the magic 8 ball |
| `!coin` | `flip`, `coinflip` | Heads or tails |
| `!choose a \| b \| c` | `pick`, `either` | Picks one option. Separate options with `\|`, or with commas if there is no `\|` |
| `!roll [max]` / `!roll [min] [max]` | `dice`, `random` | A random number, 1–6 by default |
| `!ruleta` | `raffle`, `wheel`, `spin` | The raffle. A **bouncer** types `!ruleta` to open a round; see [Ruleta](features.md#ruleta) |
| `!join` | | Enter an open ruleta round |

## Queue

| Command | Aliases | What it does |
| --- | --- | --- |
| `!escort [plays]` | `afterdj`, `escortme` | Leave the queue after your next play. `!escort 3` leaves after three more (1–20), `!escort off` cancels |
| `!bail` | `hop`, `leavequeue` | Leave the queue now; also cancels an escort |

## Moderation

Every moderation command takes an optional reason at the end. The reply shows it (`👢 Kicked Bob · spam`), and it is passed to Wavez where the server accepts one.

Quote display names with spaces: `!kick "Slow Poke" too slow`.

No one can act on the bot, on someone with the same role, or on anyone above them.

| Command | Aliases | Who | What it does |
| --- | --- | --- | --- |
| `!skip [reason]` | | bouncer | Skip the current track |
| `!kick <user> [reason]` | | bouncer | Remove someone from the room |
| `!mute <user> [duration] [reason]` | | bouncer | Mute someone, optionally for `30m`, `2h` or `1d` |
| `!unmute <user> [reason]` | | bouncer | Lift a mute |
| `!remove <user> [reason]` | `rm` | bouncer | Take someone out of the queue |
| `!move <user> <position> [reason]` | `mv` | bouncer | Move someone to a queue position (1 is first) |
| `!lock [reason]` / `!unlock [reason]` | | bouncer | Lock or unlock the queue |
| `!clear` | | bouncer | Delete the bot's own messages still in chat (from the last 100) |
| `!ban <user> [duration] [reason]` | | manager | Ban someone, optionally for `30m`, `2h` or `1d` |
| `!unban <user\|userId> [reason]` | | manager | Lift a ban |

## Custom replies

Managers can teach the bot short text replies ("canned replies") from chat. They are saved, so they survive a restart.

| Command | Aliases | Who | What it does |
| --- | --- | --- | --- |
| `!addcmd <trigger> <text> [role]` | `addcommand`, `learn` | manager | Add or replace a canned reply |
| `!delcmd <trigger>` | `delcommand`, `forget` | manager | Delete one |

```
!addcmd discord Join us at discord.gg/example
!addcmd staffonly "Meeting at 8" bouncer
```

- In the text, `{name}` becomes whoever typed the trigger and `{prefix}` becomes the prefix.
- A role name at the end limits the reply to that role and above. Without one, anyone can use it.
- Quotes around the text are optional and removed. Use them when the text itself ends with a role name: `!addcmd shout "the host"` stores `the host` for everyone, while `!addcmd bare the host` stores `the` for the host only.
- At most 50 replies of up to 300 characters each. A reply cannot reuse the name of a built-in command.
- They share a 3-second cooldown per person.
- `!help` counts them under **Canned** and `!help canned` lists them. People only see the ones they can use.
- They are not translated: they say what their author typed.

## Settings

| Command | Aliases | Who | What it does |
| --- | --- | --- | --- |
| `!cz` | `cs`, `czech`, `cesky` | manager | Switch the bot to Czech |
| `!en` | `english` | manager | Switch the bot to English |

The confirmation comes back in the new language. The choice is saved and survives a restart.
