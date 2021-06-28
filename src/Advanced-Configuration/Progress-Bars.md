# Progress Bars
![](https://i.imgur.com/LcHp0Mx.png)

### Requirements:
- Have **[PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/)** installed.
- Have the **[Progress](https://github.com/PlaceholderAPI/PlaceholderAPI/wiki/Placeholders#progress)** extension installed.
***
#### I will not explain how to make your own progress bar. Instead, I will provide you with the link to the **[Progress wiki](https://github.com/aBooDyy/Progress-Expansion)** so you can learn to make your own.

## Installation Process.
1. Install PlaceholderAPI (PAPI).
 - **[PlaceholderAPI Spigot page](https://www.spigotmc.org/resources/placeholderapi.6245/)**.
2. Install Progress extension.
 - Execute `/papi ecloud download progress`.
3. Reload PlaceholderAPI.
 - Execute `/papi reload`.

### Important Notes:
- You can't use decimals.
- As long as you use percentages, the maximum should always be `100`.
- Placeholder (external) requirements require a different usage.
  - [Explanation.](../Advanced-Configuration/Progress-Bars.md#progress-bars-with-placeholders)
- Rankup requirements that require sub-requirements will need their sub-requirements specified.
  - [Explanation.](../Advanced-Configuration/Progress-Bars.md#progress-bars-with-sub-requirements)

##### The configuration below produced [the text in the first Progress Bar image](../Advanced-Configuration/Progress-Bars.md#progress-bars).
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
### If you use Rankup's [internal/config](../Config-Placeholders.md) placeholders, they won't work outside of any Rankup context, like a scoreboard or in tab. Use Rankup's [PAPI placeholders](../PAPI-Placeholders.md#config-papi-placeholders) for that instead.
#### Rankup's config placeholder version
> `%progress_bar_{PERCENT_DONE money}_c:&d|_p:&d|_r:&3|_l:20_m:100_fullbar:&a&lCompleted!%`
#### Rankup's PAPI placeholder version
> `%progress_bar_{rankup_requirement_money_percent_done}_c:&d|_p:&d|_r:&3|_l:20_m:100_fullbar:&a&lCompleted!%`
#### Note: these two placeholders above will work identically. The only difference is that the PAPI version can be used outside of a Rankup context, like a scoreboard. Does not include MVdW placeholders, click [here](../PAPI-Placeholders.md#mvdw-placeholders) to find out how to adapt the current placeholder to work with MVdW.

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

In this case, the requirement is to kill ender dragons. [Unlike previously with `m:`, the maximum amount doesn't matter as it is a percentage](https://github.com/aBooDyy/Progress-Expansion#m).  
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
