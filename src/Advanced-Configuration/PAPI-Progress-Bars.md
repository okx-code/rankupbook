<html>
  <head>
    <meta name="description" content="Tutorial on making progress bars for rankup requirements with PAPI!">
    <meta name="keywords" content="Rankup, Minecraft, Plugin, Spigot, Prestige">
  </head>
</html>

# PAPI Progress Bars
![](https://i.imgur.com/LcHp0Mx.png)

### Requires:
- **[PlaceholderAPI](../Spigot/PAPI.html)**
***
#### I will not explain how to make your own progress bar. Instead, I will provide you with the link to the **[Progress wiki](../GitHub/Progress-Expansion.html)** so you can learn to make your own.

## Expansion Installation
1. Installing Progress Expansion
 - Execute `/papi ecloud download progress`
2. Reload PlaceholderAPI.
 - Execute `/papi reload`

### Important Notes:
- You can't use decimals.
- As long as you use percentages, the maximum should always be `100`.
- Placeholder (external) requirements require a different usage.
- Rankup requirements that require sub-requirements will need their sub-requirements specified.

##### The configuration below produced [the text in the first Progress Bar image](../Advanced-Configuration/PAPI-Progress-Bars.md#papi-progress-bars).
```yaml
rankName:
  rank: 'currentRank'
  next: 'nextRank'
  requirements:
    - 'money 5000'
    - 'xp-level 5'
  rankup:
    requirements-not-met: |-
      &4&m+                                       +
      &cYou need
      &c- &d&l$%rankup_money_formatted% &c&l- &b[%progress_bar_{PERCENT_DONE money}_c:&d|_p:&d|_r:&3|_l:20_m:100_fullbar:&a&lCompleted!%&b]
      &c- &d&l%rankup_requirement_xp-level% &5&lXP levels &c&l- &b[%progress_bar_{PERCENT_DONE xp-level}_c:&d|_p:&d|_r:&3|_l:20_m:100_fullbar:&a&lCompleted!%&b]
      &cto rankup from &7&l%rankup_current_rank%&r&c to &e&l%rankup_next_rank%&r&c!
      &4&m+                                       +
```

## Versions
### If you use Rankup's [pebble placeholders](../Placeholders.md#placeholders), they won't work outside of any Rankup context, like a scoreboard or in the tab menu. Use the [placeholders from Rankup's PAPI Expansion](../Placeholders.html#papi-placeholders) for external access.
#### Rankup's config placeholder version
> `%progress_bar_{PERCENT_DONE money}_c:&d|_p:&d|_r:&3|_l:20_m:100_fullbar:&a&lCompleted!%`
#### Rankup's PAPI placeholder version
> `%progress_bar_{rankup_requirement_money_percent_done}_c:&d|_p:&d|_r:&3|_l:20_m:100_fullbar:&a&lCompleted!%`
#### Note: these two placeholders above will work identically. The only difference is that the PAPI version can be used outside of a Rankup context, like a scoreboard.

### Progress Bars with Placeholders.
External requirements require a different approach.

`%progress_bar_{FreeRPG_globalLevel}_c:&d|_p:&d|_r:&3|_l:20_m:25000_fullbar:&a&lCompleted!%`

Instead of using the `{PERCENT_DONE <requirement>}` provided by Rankup, simply use the PAPI placeholder wrapped with `{}` instead of `%%`.  
Then for the `m:` (maximum) of the Progress placeholder, use the same number as in the `requirements:` listed in the corresponding Rankup.

###### Example Bars with Placeholders:
```yaml
rankName:
  rank: 'currentRank'
  next: 'nextRank'
  requirements:
    - 'placeholder %FreeRPG_globalLevel% >= 25000'
  rankup:
    requirements-not-met: |-
      &4&m+                                       +
      &cYou need
      &c- Global level of &d&l25K &c&l- &b[%progress_bar_{FreeRPG_globalLevel}_c:&d|_p:&d|_r:&3|_l:20_m:25000_fullbar:&a&lCompleted!%&b]
      &cto rankup from &7&l%rankup_current_rank%&r&c to &e&l%rankup_next_rank%&c!
      &4&m+                                       +
```

### Progress Bars with Sub-Requirements.
For requirements with sub-requirements, use the Rankup placeholder itself like so:  

`%progress_bar_{PERCENT_DONE mob-kills#ENDER_DRAGON}_c:&d|_p:&d|_r:&3|_l:20_m:100_fullbar:&a&lCompleted!%`  

In this case, the requirement is to kill ender dragons. [Unlike previously with `m:`, the maximum amount doesn't matter as it is a percentage](../GitHub/Progress-Examples.html).  
###### Example Bars with Sub-Requirements:
```yaml
rankName:
  rank: 'currentRank'
  next: 'nextRank'
  requirements:
    - 'mob-kills ENDER_DRAGON 7'
  rankup:
    requirements-not-met: |-
      &4&m+                                       +
      &cYou need
      &c- &d&l7 &5&lEnderdragon kills &c&l- &b[%progress_bar_{PERCENT_DONE mob-kills#ENDER_DRAGON}_c:&d|_p:&d|_r:&3|_l:20_m:100_fullbar:&a&lCompleted!%&b]
      &cto rankup from &7&l%rankup_current_rank%&r&c to &e&l%rankup_next_rank%&c!
      &4&m+                                       +
```
