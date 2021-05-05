## Using PAPI in Requirements
As mentioned on the **[Wrong Message](../Basic-Configuration-Example/Wrong-message.md)** page, Rankup supports PAPI (PlaceholderAPI) which let's you use placeholders as requirements. It's a lot easier than it sounds, so here's an example. All PAPI placeholders can be found on their **[wiki](https://github.com/PlaceholderAPI/PlaceholderAPI/wiki/Placeholders)**.
 
**IMPORTANT:** You need to download the expansion pack. If it says "NO DOWNLOAD COMMAND" then it's hardcoded into the plugin you're using and it will work regardless, Like Rankup.
 
We'll go with how many times you've jumped. We will be building on what we had after completing the **[Basic Configuration Example](../Core-Files/Basic-Configuration-Example.md)** chapter.
 
```yaml
beginner:
  rank: beginner
  next: member
  requirements:
  - 'xp-level 5'
  - 'placeholder %statistic_jump% >= 50'
  rankup:
    requirements-not-met: "&cYou have {AMOUNT_DONE xp-level}, and need {AMOUNT xp-level} xp levels to rankup!"
    gui:
      rankup:
        material: EMERALD_BLOCK
        index: 0-3
        name: '&a&lConfirm'
        lore: |-
          &6Rankup to &b{RANK}
          &eCosts {AMOUNT xp-level} xp levels.
```
 
As you can see, we've added a new requirement: `- 'placeholder %statistic_jump% >= 50'`, now let's analyze it.
* The `placeholder` part in front is necessary for Rankup to recognize that it's a placeholder.
* The `%statistic_jump%` part is the placeholder itself. Rankup will read it as how many times you've jumped thanks to PAPI.
* the `>= 50` part means that it should be `equal or greater than 50`. Basically 50 or more.

## MVdW Placeholders
Note that to use these placeholders in FeatherBoard (or likewise plugins using MVdW placeholders) you must use `{placeholderapi_placeholder}` instead of `%placeholder%`. For example, you might use `{placeholderapi_rankup_current_rank}` in FeatherBoard.

## Config PAPI Placeholders
**Note:** Placeholders are included within the Rankup plugin, a downloaded expansion is not required.

| Placeholder | Description
| ----------- | -----------
| `%rankup_current_rank%` | The rank a player is in.
| `%rankup_next_rank%` | The rank a player can rankup to.
| `%rankup_current_prestige%` | The prestige rank a player is in.
| `%rankup_next_prestige%` | The next prestige rank for the player.
| `%rankup_money%` | The money requirement for a player to /rankup.
| `%rankup_money_formatted%` | As above, but formatted. By default, this might<br>look like `1,000.00` instead of `1000.0`
| `%rankup_prestige_money%` |
| `%rankup_prestige_money_formatted%` |
| `%rankup_money_left%` |
| `%rankup_money_left_formatted%` |
| `%rankup_percent_left%` |
| `%rankup_percent_left_formatted%` |
| `%rankup_percent_done_formatted%` |
| `%rankup_percent_done_formatted%` |
| `%rankup_requirement_<requirement>[_<done/left/percent_left/percent_done>]` | The \<requirement> to /rankup. See **[requirements](https://github.com/okx-code/Rankup3/wiki/Requirements)**.<br>`%rankup_requirement_xp-level_left%` is equivalent to<br>`{AMOUNT_NEEDED xp-level}`
| `%rankup_rank_requirement_<rank>_<requirement>[_<left/percent_left/percent_done>]%` | As above, but for ranking up to a certain `<rank>`
| `%rankup_rank_money_<rank>%` | The money requirement to rankup from **<rank>**. This is formatted.
| `%rankup_rank_money_<rank>_left%` |
| `%rankup_status_<rank>%` | The status of the rank of the given rank for the player.<br>By default, returns "Complete" for rankups the player<br>has completed, "Current" for the rankup the player is<br>currently in, and "Incomplete" for rankups the player<br>has not completed.
