## How to specify sub-requirements in placeholders

Requirements that support sub-requirements are used in the format `<requirement> <sub-requirement> <amount>`. In placeholders, sub-requirements are `<requirement>#<sub-requirement>`.

For example, you might have `requirements-not-met: 'You have {AMOUNT_DONE block-break#STONE}/{AMOUNT block-break#stone}. {AMOUNT_NEEDED block-break#STONE} stone left to break.'`, or in PlaceholderAPI, `%rankup_requirement_block-break#stone%`
Use the spigot enum pages for [entities](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/package-summary.html) and [items](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/material/package-summary.html) when declared in requirements.

## List

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

# Soft-Dependent Requirements

### What are Soft-dependent Requirements?

These requirements expect another plugin dependency to be installed as well.
**If you don't have the plugin you're using a requirement from installed, THEY WILL NOT WORK**

| Name | Format | S | D | Description | Example
| ---- | ------ | ---------------- | --------- | ----------- | -------
| `placeholder` |  `%placeholder% <operation> string`.<br>Operation can be any of:<br>`=`, `<`, `>`, `<=`, `>=`, `==` | no | no | Compares the PAPI<br>with the string<br>via the operation.<br>`==` doesn't convert<br>the data type of<br>the string<br>or placeholder. | `placeholder %server_tps% >= 19`
| `mcmmo` | [skillname](https://github.com/mcMMO-Dev/mcMMO-API/blob/master/src/main/java/com/neetgames/mcmmo/skill/CorePrimarySkillType.java) number | yes | no | Requires a player to have<br>a certain level in an<br>[McMMO Skill](https://github.com/mcMMO-Dev/mcMMO-API/blob/master/src/main/java/com/neetgames/mcmmo/skill/CorePrimarySkillType.java) [also named here](https://docs.google.com/document/d/1qY6hEyGCO5z1PRup_OvMBxAmumydxxoO_H-pnUrVK8M/edit#heading=h.nhed81k1qlj7). | `mcmmo archery 1000`
| `mcmmo-power-level` | number | no | no | Requires a player to have<br>a certain power level in McMMO. | `mcmmo-power-level 500`
| `advancedachievements-achievement` | text | no | no | At least one<br>of certain<br>advanced achievements,<br>separated by spaces. | `advancedachievements-achievement own_shop start_town`
| `advancedachievements-total` | text | no | no | The total number of advanced<br>achievements a player has. | `advancedachievements-total 20`
| `votingplugin-votes` | text | no | no | The amount of votes<br>a player has,<br>counted by VotingPlugin. |  `votingplugin-votes 10`
| `towny-resident` | true/false | no | no | Requires a player to<br>(not) be a resident of a town. |  `towny-resident true`
| `towny-mayor` | true/false | no | no | Requires a player to<br>(not) be a mayor of a town. |  `towny-mayor true`
| `towny-king` | true/false | no | no | Requires a player to<br>(not) be a king of a nation. |  `towny-king true`
| `towny-mayor-residents` | number | no | no | The amount of residents<br>a player's town has (need to be mayor). |  `towny-mayor-residents 10`
| `towny-king-residents` | number | no | no | The amount of residents<br>a player's nation has (need to be king). |  `towny-king-residents 10`
| `towny-king-towns` | number | no | no | The amount of towns a player's<br>nation has (need to be king). |  `towny-king-towns 10`
| `tokenmanager-tokens` | number | no | yes | The amount of tokens from<br>the plugin [TokenManager](https://www.spigotmc.org/resources/tokenmanager.8610/). | `tokenmanager-tokens 10`
| `tokenmanager-tokensh` | number | no | no | As above,<br>without deduction | `tokenmanager-tokensh 10`

<!-- <sup><a id="ref_3" href="#ref_3">3</a></sup>not released on SpigotMC yet. Pre-release builds can be downloaded on [Jenkins](https://ci.okx.sh/job/Rankup3/) or on the [Discord server](https://discord.gg/maB4382). -->
