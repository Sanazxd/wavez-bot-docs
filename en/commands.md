# Commands

🇨🇿 [Česky](../cs/commands.md) · [← Back](README.md)

The prefix is `!` unless the room sets another one. `<angle brackets>` are required, `[square brackets]` optional, and `a | b` means either form.

An alias works exactly like the command name: `!whois` is `!user`.

**Who** is the lowest role that can use the command; see [Roles](roles.md). Commands without a role are open to everyone.

**Cooldowns** are per person. Moderation and settings commands, `!ping` and `!ruleta` wait 5 seconds between uses, `!clear` waits 10, and every other command 3.

**Replies** to commands are deleted after a minute; see [A tidy chat](features.md#a-tidy-chat).

## Info

| Command | Aliases | What it does |
| --- | --- | --- |
| `!help [category\|command]` | `commands` | With nothing after it, the categories you can use with a count each, and a link to this documentation. `!help fun` lists a category, `!help seen` explains a command. Categories also work by their Czech names (`!help zábava`) |
| `!users` | `active`, `pop` | How many people are in the room (the bot not counted), and which of them are AFK |
| `!user <name>` | `whois`, `profile` | Someone's Wavez profile: platform title, level, fans, country flag |
| `!seen <user>` | `lastseen` | When someone last spoke and what they last played |
| `!afk [reason]` | `away`, `brb` | Mark yourself away. See [AFK](features.md#afk) |
| `!uptime` | | How long the bot has been running |
| `!ping` | `pong` | Checks the bot is alive, with the round trip to the server in ms |

## Fun

| Command | Aliases | What it does |
| --- | --- | --- |
| `!8ball <question>` | `eightball` | Ask the magic 8 ball |
| `!coin` | `flip`, `coinflip` | Heads or tails |
| `!choose a \| b \| c` | `pick`, `either` | Picks one option. Separate options with `\|`, or with commas if there is no `\|` |
| `!roll [max]` / `!roll [min] [max]` | `dice`, `random` | A random number, 1–6 by default |
| `!ruleta` | `raffle`, `wheel`, `spin` | The raffle. A **manager** types `!ruleta` to open a round; see [Ruleta](features.md#ruleta) |
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
| `!move <user> <position> [reason]` | `mv` | bouncer | Move someone in the queue to a position (1 is first; past the end puts them last). Says so only once the server has done it |
| `!lock [reason]` / `!unlock [reason]` | | bouncer | Lock or unlock the queue |
| `!clear` | | bouncer | Delete the bot's own messages still in chat (from the last 100) |
| `!ban <user> [duration] [reason]` | | manager | Ban someone, optionally for `30m`, `2h` or `1d` |
| `!unban <user\|userId> [reason]` | | manager | Lift a ban |

## Settings

| Command | Aliases | Who | What it does |
| --- | --- | --- | --- |
| `!cz` | `cs`, `czech`, `cesky` | manager | Switch the bot to Czech |
| `!en` | `english` | manager | Switch the bot to English |

The confirmation comes back in the new language. The choice is saved and survives a restart.
