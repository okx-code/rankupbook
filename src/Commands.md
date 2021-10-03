<html>
  <head>
    <meta name="description" content="Reference for all commands provided by Rankup3.">
    <meta name="keywords" content="Rankup, Minecraft, Plugin, Spigot, Prestige, Commands">
  </head>
</html>

# Player Commands
> The following commands are available to [all players, OPs, and console by default](./GitHub/Rankup3/plugin/Player.html).  
> Rankup3's commands are available after the plugin is [enabled](./GitHub/Rankup3/Java/EnableRankupPlugin.html) by your server.  
> Only run commands after the server has finished starting up.  

Command         | permission         | config                                                  | Description                                                      | For Developers
-               | -                  | -                                                       | -                                                                | -
`/rankup`       | `rankup.rankup`    | N/A                                                     | <!-- Roll Credits -->The primary progression command. Checks a player has met the `requirements:` then moves a player up the rankup ladder. | [Implementation](./GitHub/Rankup3/Java/commands/RankupCommand.html)
`/ranks`        | `rankup.ranks`     | [`ranks:`](./GitHub/Rankup3/config/Ranks.html)          | Displays the entire rankup ladder relative to the player's current step. | [Implementation](./GitHub/Rankup3/Java/commands/RanksCommand.html)
`/maxrankup`    | `rankup.maxrankup` | [`max-rankup:`](./GitHub/Rankup3/config/MaxRankup.html) | Will rankup the player as many times as possible and without displaying confirmation windows until they fail to meet the `next` rankup step's requirements or complete the ladder. | [Implementation](./GitHub/Rankup3/Java/commands/MaxRankupCommand.html)
`/prestige`     | `rankup.prestige`  | [`prestige:`](./GitHub/Rankup3/config/Prestige.html)    | The secondary progression command. Checks a player has met the `requirements:` then moves a player up the prestige ladder. | [Implementation](./GitHub/Rankup3/Java/commands/PrestigeCommand.html)
`/prestiges`    | `rankup.prestiges` | [`prestiges:`](./GitHub/Rankup3/config/Prestiges.html)  | Displays the entire prestiges ladder relative to the player's current step. | [Implementation](./GitHub/Rankup3/Java/commands/PrestigesCommand.html)

# Admin Commands

> The following commands are only available to [OPs and console by default](./GitHub/Rankup3/plugin/Admin.html).  
> If OPs are disabled, a player with `rankup.admin` will get the same affect as being an OP.
> Specifically, `rankup.admin` grants [`rankup.checkversion`, `rankup.reload`, `rankup.force`, and `rankup.notify`](./GitHub/Rankup3/plugin/Admin.html).
> The plugin used to be called PrisonRankup, which is why [`/pru` is still an alias for `/rankup3`](./GitHub/Rankup3/plugin/PRU.html).  
> Therefore, any `/rankup3` command can substitute `rankup3` for `pru`, like `/pru reload`.  

Command                                    | permission            | Description | For Developers
-                                          | -                     | -           | -
N/A                                        | `rankup.notify`       | This permission determines whether a player joining the server is notified of new updates. | [Implementation](https://github.com/okx-code/Rankup3/blob/master/src/main/java/sh/okx/rankup/RankupPlugin.java#L175)
`/rankup3`                                 | `rankup.info`         | The base command for rankup3. It prints helpful information like a list of commands and version information. | [Implementation](./GitHub/Rankup3/Java/commands/InfoCommand.html)
`/rankup3`                                 | `rankup.checkversion` | This permission determines whether a player running `/rankup3` is notified of new updates. | [Implementation](./GitHub/Rankup3/Java/commands/InfoCommand/checkversion.html)
`/rankup3 reload`                          | `rankup.reload`       | Reloads the `rankups.yml`, `prestiges.yml`, and selected locale while the server is running. This allows for rapidly testing changes to your files. [See FAQ for more information.](./FAQ.html#when-executing-rankup3-reload-what-actually-gets-reloaded) | [Implementation](./GitHub/Rankup3/Java/commands/InfoCommand/reload.html)
`/rankup3 forcerankup <player>`            | `rankup.force`        | Moves the specified player up the rankup ladder regardless of requirements. | [Implementation](./GitHub/Rankup3/Java/commands/InfoCommand/forcerankup.html)
`/rankup3 forceprestige <player>`          | `rankup.force`        | Moves the specified player up the prestige ladder regardless of requirements. | [Implementation](./GitHub/Rankup3/Java/commands/InfoCommand/forceprestige.html)
`/rankup3 rankdown <player>`               | `rankup.force`        | Moves the specified player down the rankup ladder. | [Implementation](./GitHub/Rankup3/Java/commands/InfoCommand/rankdown.html)
`/rankup3 playtime get <player>`           | `rankup.playtime`<br>or<br>`rankup.playtime.get` | Prints the player's total playtime. | [Implementation](./GitHub/Rankup3/Java/commands/InfoCommand/playtime-get.html)
`/rankup3 playtime set <player> <minutes>` | `rankup.playtime`     | Modifies the player's total playtime using the minecraft statistic. | [Implementation](./GitHub/Rankup3/Java/commands/InfoCommand/playtime-set.html)
`/rankup3 playtime add <player> <minutes>` | `rankup.playtime`     | Modifies the player's total playtime using the minecraft statistic. | [Implementation](./GitHub/Rankup3/Java/commands/InfoCommand/playtime-add.html)

# Debug Commands
> The following commands are also only available to [OPs and console by default](./GitHub/Rankup3/plugin/Admin.html).  
> However, unlike the prior [Admin Commands](#admin-commands) these were introduced in version 3.9 and are not presented by autofill, so must be called explicitly.* (unconfirmed)  

Command                 | permission     | Description | For Developers
-                       | -              | -           | -
`/rankup3 placeholders` | `rankup.admin` | Prints the current value of each PAPI placeholder provided by Rankup3. Intended for use in-game. Values are blank when called from console since each PAPI has no target.| [Implementation](./GitHub/Rankup3/Java/commands/InfoCommand/placeholders.html)
`/rankup3 tree`         | `rankup.admin` | Displays both the rankup and prestige ladder as identified by Rankup3 internally, without messages or player-progression-state information. Useful for verifying the integrity of your file when only messages are throwing errors. | [Implementation](./GitHub/Rankup3/Java/commands/InfoCommand/tree.html)
