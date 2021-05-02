# List

**S means "supports sub-requirements?". D means "is deductible?".**

| Name | Format | S | D | Description | Example
| ---- | ------ | ---------------- | --------- | ----------- | -------
| `money` | number | no | yes | Checks the player's balance and takes the specified amount when ranking up. | `money 1000`
| `moneyh` | number | no | no | Checks the player's balance but does not take the money. | `moneyh 10000`
| `xp-level` | number | no | yes | Checks the player's xp-levels for the specified amount and takes it. | `xp-level 30`
| `xp-levelh` | number | no | no | Checks the player's xp-levels for the specified amount but does not take them. | `xp-levelh 50`
| `playtime-minutes` | number | no | no | How long a player has been online, in minutes (uses the Minecraft statistic). | `playtime-minutes 120`
| `group` | text | no | no | Requires a player to be in at least one of a list of groups, separated by spaces. | `group vip mvp`
| `permission` | text | no | no | Requires player to have at least one of a list of permissions, separated by spaces. | `permission permission.one permission.two`
| `world` | text | no | no | Requires a player to be in any of the worlds listed, separated by spaces. | `world my_world_nether my_world_the_end`
| `player-kills` | number | no | no | Players killed. Uses the Minecraft statistic. | `player-kills 15`
| `total-mob-kills` | number | no | no | The total amount of mob kills a player has | `total-mob-kills 500`
| `mob-kills` | number | yes | no | [Mobs](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/package-summary.html) of the specified type killed. Uses the Minecraft statistic. | `mob-kills Skeleton 100`
| `item` | number | yes | yes | The amount of [items](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html) a player currently has | `item DIAMOND 64`
| `itemh` | number | yes | no | As prior, but does not deduct [items](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html) from the player | `itemh GLASS 64`
| `use-item` | number | yes | no | The amount of times a player has used an [item](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html). | `use-item DIAMOND_SWORD 200`
| `block-break` | number | yes | no | The amount of times a player has broken a [block](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html) | `block-break STONE 1000`
| `craft-item` | number | yes | no | The amount of times a player has crafted an [item](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html) | `craft-item STONE_BRICKS 256`
| `advancement` | text | no | no | Checks for a specific Minecraft [advancement](https://minecraft.fandom.com/wiki/Advancement#List_of_advancements) | `advancement story/obtain_armor`
