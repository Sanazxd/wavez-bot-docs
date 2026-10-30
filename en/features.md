# Features

🇨🇿 [Česky](../cs/features.md) · [← Back](README.md)

What the bot does on its own, without anyone typing a command.

## Welcomes

When someone arrives, the bot greets them by @-mention. These get their own, bigger greetings:

- the room host
- staff: bouncers, managers and co-hosts
- resident DJs
- VIPs

Everyone else gets the plain welcome.

- Each special greeting has several lines. The bot picks one at random and never repeats the line it used last.
- A special greeting waits an hour before it repeats. Someone who comes back within the hour gets the plain welcome.
- Only the role the room gave someone counts. A platform title such as admin or ambassador does not earn a special greeting on its own.
- Bots are never greeted.
- Every real arrival is greeted, including someone coming back after closing the tab or losing their connection.
- The bot does not greet people who were already in the room. Wavez sometimes repeats a join for them, or lists staff who are offline.

## Farewells

When someone leaves the room, including through a kick or ban, the bot says goodbye.

- The farewell is deleted after an hour, or as soon as the person comes back.
- Only the latest welcome or farewell for each person stays in chat. A new one about someone takes down the previous one about them, so a flaky connection does not fill the chat.
- Someone who closes the tab sends no "left" signal. The bot notices them missing from the room list, or Wavez's own log of joins and leaves shows them leaving, and says the farewell then. It checks both every 30 seconds.
- A connection that only blips (a background tab, a Wi-Fi switch) is not a leave. Someone out of the room for less than a minute, and not logged by Wavez as leaving, gets no farewell, and no new welcome when they are back.

## AFK

`!afk` marks you away, and `!afk <reason>` adds a reason (up to 80 characters). The bot posts an away notice starting with `:brb:`.

- **Mentions while you are away:** anyone who @-mentions you is told how long you have been away and why. Each person hears this at most once every 5 minutes.
- **Coming back:** the next time you write in chat, you are back. The bot welcomes you back with how long you were gone and who asked for you. That message disappears after 15 seconds.
- **Commands while away:** `!afk` alone ends your AFK, and `!afk <new reason>` changes the reason.
- **Cleanup:** once you are back, the bot's away notice and its replies to mentions are deleted. A changed reason takes the old notice down straight away.
- **Leaving:** leaving the room ends your AFK quietly, with no welcome back when you return. So does the bot finding you gone when it starts.
- **Status:** `!users` shows who in the room is AFK.

## Ruleta

A raffle whose winner jumps to the front of the queue.

1. A **manager** types `!ruleta`. The bot announces the round to `@everyone`, without tagging or replying to the manager, and opens a 1-minute window to join.
2. Anyone types `!join` to enter. Someone already in is reminded once; repeating `!join` after that does nothing, so it cannot be spammed. `!join` with no round open does nothing either. There is no leaving: an entry stays in until the draw.
3. When the minute is up, the bot draws a winner at random and announces them.
4. The winner is added to the queue if they are not in it, then moved to position 1. The announcement says where they came from, e.g. "moved from #5 to #1".

- **The DJ wins:** if the draw lands on whoever is playing at that moment, the bot says so and draws again from everyone else. If the DJ was the only entrant, nobody wins.
- **Nobody joined:** the bot says so.
- **Winner left:** if the winner cannot be queued (for example because they left), they are still announced but nobody is moved.

## Auto-skip

The bot skips a track the room clearly does not like: once mehs are at least half of all woots and mehs (4 mehs to 4 woots, or 1 meh to none). Grabs do not count.

- It never skips in the first 30 seconds of a track, and acts at most once per track.
- It posts the tally when it skips: `⏭️ Auto-skipped · 👍 4 · 👎 4`.

## Emote train

When 3 different people post the same emote (`:kong:` by default) within 2 minutes of each other, the bot joins in with a burst of 5 to 15 of them.

- After that it counts again from zero.
- It waits at least 15 seconds between bursts.
- The bursts stay in chat; they are not deleted after an hour.
- Commands and bots do not count.

## Crowd celebration

When a join brings the room to 10 people (bots not counted), the bot celebrates with a random line. The cheer is for the whole room, so it tags nobody.

It does not celebrate again until the room has dropped to 8 or fewer and 3 hours have passed. It does not celebrate a room that is already at 10 when the bot starts.

## A tidy chat

- **Commands are deleted** once they have been answered. This covers anything starting with `!`, typos and unknown commands included.
- **Replies to commands are deleted** after 1 minute. `!clear` confirmations go after 10 seconds. The `!afk` notice stays until you are back, at most an hour.
- **The bot's other messages are deleted** after an hour: welcomes, farewells, ruleta announcements and the like. The AFK welcome back goes after 15 seconds, and the startup line after a minute. Emote train bursts stay.
- **`!clear`** lets a bouncer delete everything the bot still has in chat.
- **Long replies** are split into up to four numbered messages (`(1/3)`), because Wavez rejects messages over 255 characters.

## Startup line

When the bot comes online and is ready to answer, it posts a short line, by default pointing at `!help`. The line is deleted after a minute.

## Reply style

Every reply follows the same layout so the room learns to scan it:

- one emoji up front saying what kind of answer it is (`🕘` last seen, `👤` profile, `🎧` queue, `⚠️` a mistake or a usage hint)
- ` · ` between items, `, ` between names
- `Title — Artist` for a track

```
🕘 Ann: spoke 5m ago · played Blue Veins — Ash Walker 2h ago
👤 @ann · lvl 12 · 40 fans · 🇨🇿
👥 14 listening · 💤 afk: Bo, Cy
```

## What is remembered across restarts

The bot remembers these through a restart:

- AFK flags
- who last spoke and what they last played
- escort bookings
- the chosen language
- the ruleta pool

Vote counts are not saved, so after a restart auto-skip waits for the next vote before it can judge a track.
