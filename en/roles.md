# Roles

🇨🇿 [Česky](../cs/roles.md) · [← Back](README.md)

## The ladder

From lowest to highest:

```
user < vip < resident_dj < bouncer < manager < cohost < host
```

A command for a role is open to that role and everyone above it. "Bouncer" means bouncers, managers, co-hosts and the host.

| Role | What it unlocks in the bot |
| --- | --- |
| user | every info, fun and queue command |
| vip | its own welcome; no extra powers |
| resident_dj | its own welcome; no extra powers |
| bouncer | skip, kick, mute, unmute, remove, move, lock and unlock, `!clear` |
| manager | ban, unban, `!en`, `!cz`, opening a ruleta round |
| cohost, host | everything above |

## Who can act on whom

Beyond the role a command needs:

- no one can kick, ban, mute, move or remove the bot
- no one can act on someone with the same role
- no one can act on anyone above them

A bouncer cannot kick another bouncer or a manager, but can kick a VIP or a resident DJ.

## Unknown roles

If Wavez reports a role for a person that the bot does not know (for example after a rename on Wavez's side), that person gets no powers, and no one can kick, ban or mute them through the bot. This way a renamed role never becomes a loophole.

## Platform titles

Wavez also has platform-wide titles such as `admin` and `ambassador`. On their own they mean nothing in a room: an ambassador with no room role is a `user` here.

The bot counts one of them as a room role:

| Platform title | Counts as |
| --- | --- |
| `admin` | manager |

- Whichever role is higher wins, so nobody is demoted: an admin who is also the host stays host.
- It protects as well as grants: a plain bouncer cannot kick an admin.
- Ambassadors are whatever role the room gave them. An ambassador with no room role is a `user`, even though Wavez reports them to the bot as a manager.
- Other titles, such as `subscriber`, mean nothing to the bot.
- Titles do not change the welcome. Admins and ambassadors get the welcome for their room role, so the plain one if they have none.

`!user <name>` shows the titles an account holds.
