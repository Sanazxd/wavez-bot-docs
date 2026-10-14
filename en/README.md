# Wavez Bot

🇨🇿 [Česky](../cs/README.md)

Wavez Bot answers commands in a [Wavez.fm](https://wavez.fm) room's chat, greets people as they arrive, runs the ruleta raffle and gives staff moderation tools. It speaks English and Czech.

It is a fork of [fluteds/wavez-bot](https://github.com/fluteds/wavez-bot), the original project by fluteds. See the [changelog](changelog.md) for what is different.

## In the room

Type `!help` in chat. The bot lists the command categories you can use and how many commands each has. From there:

- `!help fun` lists the commands in one category
- `!help np` explains one command, with its usage and who can use it

You only see what your role lets you use, so regular users never see the moderation commands.

Commands you type are deleted once the bot has answered, and the bot's own messages disappear after an hour, so the chat stays readable.

## Pages

| Page | What is in it |
| --- | --- |
| [Commands](commands.md) | every command with its aliases, usage and minimum role |
| [Features](features.md) | what the bot does without being asked: welcomes, AFK, ruleta, auto-skip, emote train |
| [Roles](roles.md) | the role ladder, VIP, platform titles, who can act on whom |
| [Changelog](changelog.md) | this fork compared with the original |

## Language

The bot speaks English or Czech. A manager or above switches it with `!en` or `!cz`, and the choice survives a restart.
