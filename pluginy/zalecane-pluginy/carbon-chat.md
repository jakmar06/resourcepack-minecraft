---
description: W tej sekcji poznasz komendy, permisje i konfiguracje pluginu carbon chat.
hidden: true
---

# Carbon Chat

## Komendy Pluginu

The following is a list of commands offered by the plugin, and their function.

| Komendy                    | Alliasy                             | Permisje                  | Opis                                                                                                   |
| -------------------------- | ----------------------------------- | ------------------------- | ------------------------------------------------------------------------------------------------------ |
| `/clearchat`               | `/cc`, `/chatclear`                 | `carbon.clearchat.clear`  | Clears the chat for all players except those with `carbon.chearchat.exempt`.                           |
| `/join <channel>`          | None                                | `carbon.join`             | Joins available channels.                                                                              |
| `/leave <channel>`         | None                                | `carbon.leave`            | Leaves joined channels.                                                                                |
| `/ignore <player>`         | `/block`                            | `carbon.ignore`           | Hides all chat messages and whispers from the specified player.                                        |
| `/unignore <player>`       | `/unblock`                          | `carbon.ignore.unignore`  | Removes a player from the sender's ignore list.                                                        |
| `/ignorelist <page>`       | `/listignores`                      | `carbon.ignore`           | Shows list of ignored users.                                                                           |
| `/spy`                     | None                                | `carbon.spy`              | Allows a player to view all private and channel messages they otherwise wouldn't see.                  |
| `/mute <player>`           | None                                | `carbon.mute`             | Mutes a player, preventing them from sending messages or whispers.                                     |
| `/unmute <player>`         | None                                | `carbon.mute.unmute`      | Unmutes a player, allowing them to use chat and send whispers.                                         |
| `/muteinfo <player>`       | `/muted`                            | `carbon.mute.info`        | Shows if a player is muted or not.                                                                     |
| `/nickname <player>`       | `/nick`                             | `carbon.nickname`         | Shows a player's nickname.                                                                             |
| `/nickname --player`       | `/nick`                             | `carbon.nickname.others`  | Checks/sets other players' nicknames.                                                                  |
| `/nickname --nickname`     | `/nick`                             | `carbon.nickname.set`     | Sets your/other players' nicknames.                                                                    |
| `/nickname --reset`        | `/nick`                             | `carbon.nickname.set`     | Resets your/other players' nicknames.                                                                  |
| `/updateusername <player>` | `/updatename`                       | `carbon.updateusername`   | Updates your/other players' username by fetching profile data again.                                   |
| `/carbon reload`           | None                                | `carbon.reload`           | Reloads Carbon's config, channel settings, and translations.                                           |
| `/filter`                  | None                                | `carbon.filter`           | Toggles defined optional chat filter. See here(Basic-Configuration#optional-chat-filter) for info.     |
| `/reply`                   | `/r`                                | `carbon.whisper.reply`    | Sends a message to the last player who messaged you.                                                   |
| `/continue`                | `/c`                                | `carbon.whisper.continue` | Sends a message to the last player whispered.                                                          |
| `/whisper <player>`        | `/w`, `message`, `msg`, `m`, `tell` | `carbon.whisper`          | Sends a private message to another player.                                                             |
| `/togglemsg`               | `/togglepm`                         | `carbon.togglemsg`        | Hides/shows incoming private messages.                                                                 |
| `/carbondebug`             | `/cdebug`                           | `carbon.debug`            | Allows the sender to quickly check what carbon thinks the player's primary and non-primary groups are. |
| `/carbon help`             | None                                | `carbon.help`             | Command description.                                                                                   |

`<player>` in `/ignore`, `/unignore`, `/mute`, `/unmute`, `/muteinfo` and `/updateusername` can be replaced with UUID if the `-u` or `--uuid` flag is used. Example: `/mute --uuid f84c6a79-44e4-4d98-8ca7-7d6dd8bb3c64`.
