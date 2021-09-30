<html>
  <head>
    <meta name="description" content="Reference table of Requirements including all built-ins and Soft-Dependent requirements.">
    <meta name="keywords" content="Rankup, Minecraft, Plugin, Spigot, Prestige">
  </head>
</html>

## List
If a player doesn't have enough to meet any `D=yes` requirement, none will be taken.
#### Scroll down for soft-dependent requirements.

> **`S` means "supports sub-requirements?".**<br>
> **`D` means "is deductible?".**

| Name | Format | S | D | Description | Example
| ---- | ------ | ---------------- | --------- | ----------- | -------
| `money` | number | no | yes | Takes the specified amount<br>from the player's balance. | `money 1000`
| `moneyh` | number | no | no | Checks the player's balance for<br>at least the specified amount. | `moneyh 10000`
| `xp-level` | number | no | yes | Takes the specified amount of<br>xp-levels from the player. | `xp-level 30`
| `xp-levelh` | number | no | no | Checks the player's xp-levels for<br> at least the specified amount. | `xp-levelh 50`
| `playtime-minutes` | number | no | no | How long a player has<br>been online, in minutes.<br>Uses the Minecraft statistic. | `playtime-minutes 120`
| `group` | text | no | no | Requires a player to be in<br>at least one of a list of<br>groups, separated by spaces. | `group vip mvp`
| `permission` | text | no | no | Requires player to have at least<br>one of a list of permissions,<br>separated by spaces. | `permission permission.one permission.two`
| `world` | text | no | no | Requires a player to be in<br>any of the worlds listed,<br>separated by spaces. | `world my_world_nether my_world_the_end`
| `player-kills` | number | no | no | Players killed.<br>Uses the Minecraft statistic. | `player-kills 15`
| `total-mob-kills` | number | no | no | The total amount of<br>mob kills a player has. | `total-mob-kills 500`
| `mob-kills` | number | yes | no | [Mobs](./Spigot/Docs/mobs.html) of the<br>specified type killed.<br>Uses the Minecraft statistic. | `mob-kills Skeleton 100`
| `item` | number | yes | yes | The amount of [items](./Spigot/Docs/materials.html)<br>a player currently has. | `item DIAMOND 64`
| `itemh` | number | yes | no | As prior, but<br>does not deduct the [items](./Spigot/Docs/materials.html). | `itemh GLASS 64`
| `use-item` | number | yes | no | The amount of times<br>a player has used an [item](./Spigot/Docs/materials.html). | `use-item DIAMOND_SWORD 200`
| `block-break` | number | yes | no | The amount of times<br>a player has broken a [block](./Spigot/Docs/materials.html) | `block-break STONE 1000`
| `craft-item` | number | yes | no | The amount of times<br>a player has crafted an [item](./Spigot/Docs/materials.html) | `craft-item STONE_BRICKS 256`
| `advancement` | text | no | no | Checks for a specific<br>Minecraft [advancement](./Minecraft/Wiki/Advancements.html) | `advancement story/obtain_armor`

## Soft-Dependent Requirements

### What are Soft-dependent Requirements?

These requirements expect another plugin dependency to be installed as well.
**If you don't have the plugin you're using a requirement from installed, THEY WILL NOT WORK**

| Name | Format | S | D | Description | Example
| ---- | ------ | ---------------- | --------- | ----------- | -------
| `placeholder` | text | no | no | Operation can be any of:<br>`=`, `<`, `>`, `<=`, `>=`, `==`<br>Compares the PAPI with the<br>string via the operation.<br>`=` doesn't convert<br>the data type of<br>the string<br>or placeholder.<br>All other operations will<br>convert to a double first. | `placeholder %papi_placeholder% <operation> string`<br>`placeholder %server_tps% >= 19`
| `mcmmo` | number | yes | no | Requires a player to have<br>a certain level in an<br>[McMMO Skill](./GitHub/McMMO/CorePrimarySkillTypes.html) [also named here](./GitHub/McMMO/DesignDoc.html). | `mcmmo skillname number`<br>`mcmmo archery 1000`
| `mcmmo-power-level` | number | no | no | Requires a player to have<br>a certain power level in McMMO. | `mcmmo-power-level 500`
| `advancedachievements-achievement` | text | no | no | At least one<br>of certain<br>advanced achievements,<br>separated by spaces. | `advancedachievements-achievement own_shop start_town`
| `advancedachievements-total` | text | no | no | The total number of advanced<br>achievements a player has. | `advancedachievements-total 20`
| `votingplugin-votes` | text | no | no | The amount of votes<br>a player has,<br>counted by VotingPlugin. |  `votingplugin-votes 10`
| `towny-resident` | bool | no | no | Requires a player to<br>(not) be a resident of a town. |  `towny-resident true`
| `towny-mayor` | bool | no | no | Requires a player to<br>(not) be a mayor of a town. |  `towny-mayor true`
| `towny-king` | bool | no | no | Requires a player to<br>(not) be a king of a nation. |  `towny-king true`
| `towny-mayor-residents` | number | no | no | The amount of residents<br>a player's town has<br>(need to be mayor). |  `towny-mayor-residents 10`
| `towny-king-residents` | number | no | no | The amount of residents<br>a player's nation has<br>(need to be king). |  `towny-king-residents 10`
| `towny-king-towns` | number | no | no | The amount of towns a<br>player's nation has<br>(need to be king). |  `towny-king-towns 10`
| `tokenmanager-tokens` | number | no | yes | The amount of tokens from<br>the plugin [TokenManager](./Spigot/TokenManager.html). | `tokenmanager-tokens 10`
| `tokenmanager-tokensh` | number | no | no | As above,<br>without deduction | `tokenmanager-tokensh 10`
