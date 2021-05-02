# Soft-Dependent Requirements

### What are Soft-dependent Requirements?

These requirements expect another plugin dependency to be installed as well.
**If you don't have the plugin you're using a requirement from installed, THEY WILL NOT WORK**

| Name | Format | S | D | Description | Example
| ---- | ------ | ---------------- | --------- | ----------- | -------
| `placeholder` |  `%placeholder% <operation> string`. Operation can be any of: `=`, `<`, `>`, `<=`, `>=`, `==` | no | no | Compares the PlaceholderAPI placeholder with the string via the operation. `=` works with string placeholders and must match **exactly** (`==` uses numbers). The other operations convert the string and the placeholder to a number first. Prefer the `>=` placeholder where possible. | `placeholder %server_tps% >= 19`
| `mcmmo` | [skillname](https://github.com/mcMMO-Dev/mcMMO-API/blob/master/src/main/java/com/neetgames/mcmmo/skill/CorePrimarySkillType.java) number | yes | no | Requires a player to have a certain level in an [McMMO Skill](https://github.com/mcMMO-Dev/mcMMO-API/blob/master/src/main/java/com/neetgames/mcmmo/skill/CorePrimarySkillType.java) [also named here](https://docs.google.com/document/d/1qY6hEyGCO5z1PRup_OvMBxAmumydxxoO_H-pnUrVK8M/edit#heading=h.nhed81k1qlj7). | `mcmmo archery 1000`
| `mcmmo-power-level` | number | no | no | Requires a player to have a certain power level in McMMO. | `mcmmo-power-level 500`
| `advancedachievements-achievement` | text | no | no | At least one of certain advanced achievements, separated by spaces. | `advancedachievements-achievement own_shop start_town`
| `advancedachievements-total` | text | no | no | The total number of advanced achievements a player has. | `advancedachievements-total 20`
| `votingplugin-votes` | text | no | no | The amount of votes a player has, counted by VotingPlugin. |  `votingplugin-votes 10`
| `towny-resident` | true/false | no | no | Requires a player to (not) be a resident of a town. |  `towny-resident true`
| `towny-mayor` | true/false | no | no | Requires a player to (not) be a mayor of a town. |  `towny-mayor true`
| `towny-king` | true/false | no | no | Requires a player to (not) be a king of a nation. |  `towny-king true`
| `towny-mayor-residents` | number | no | no | The amount of residents a player's town has (need to be mayor). |  `towny-mayor-residents 10`
| `towny-king-residents` | number | no | no | The amount of residents a player's nation has (need to be king). |  `towny-king-residents 10`
| `towny-king-towns` | number | no | no | The amount of towns a player's nation has (need to be king). |  `towny-king-towns 10`
| `tokenmanager-tokens` | number | no | yes | The amount of tokens from the plugin [TokenManager](https://www.spigotmc.org/resources/tokenmanager.8610/). | `tokenmanager-tokens 10`
| `tokenmanager-tokensh` | number | no | no | As above, but without deducting tokens | `tokenmanager-tokensh 10`
