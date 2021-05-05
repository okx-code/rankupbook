# Change Requirement Chat Color When Completed!

![](https://i.imgur.com/zK1aybS.png)

The config that you see above. all in the `rankups.yml`!
```yaml
    requirements-not-met: |-
      &4&m+                                       +
      &cYou need
      &c- &d&l$%rankup_money_formatted% &c&l- &b[%progress_bar_{PERCENT_DONE money}_c:&d|_p:&d|_r:&3|_l:20_m:100_fullbar:&a&lCompleted!%&b]
      &c- &d&l$%rankup_money_formatted% &c&l- %progress_bar_{AMOUNT_DONE money}_p:&b{AMOUNT_DONE money}_l:1_m:{AMOUNT money}_fullbar:&d{AMOUNT money}%&d/&d{AMOUNT money}
      &c- &d&l%rankup_requirement_xp-level% &5&lXP levels &c&l- &b[%progress_bar_{PERCENT_DONE xp-level}_c:&d|_p:&d|_r:&3|_l:20_m:100_fullbar:&a&lCompleted!%&b]
      &cto rankup from &7&l%rankup_current_rank%&r&c to &e&l%rankup_next_rank%&r&c!
      &4&m+                                       +
```

#### The important bit:
**Note: This placeholder uses the `money` requirement.** Here are the instructions to **[change it](#change-the-requirement-itself)**.
```yaml
%progress_bar_{AMOUNT_DONE money}_p:&b{AMOUNT_DONE money}_l:1_m:{AMOUNT money}_fullbar:&d{AMOUNT money}%&d/&d{AMOUNT money}
```

## Installation Process.
#### 1. Install PlaceholderAPI (PAPI).
###### - **[PlaceholderAPI Spigot page](https://www.spigotmc.org/resources/placeholderapi.6245/)**.
#### 2. Install Progress extension.
###### - Execute `/papi ecloud download progress`.
#### 3. Reload PlaceholderAPI.
###### - Execute `/papi reload`.

## Versions
### If you use Rankup's [internal/config](../Core-Files/Config-Placeholders.md) placeholders, they won't work outside of any Rankup context, like a scoreboard or in tab. Use Rankup's [PAPI placeholders](../Core-Files/PAPI-Placeholders.md#config-papi-placeholders) for that instead.
#### Rankup's config placeholder version
> `%progress_bar_{AMOUNT_DONE money}_p:&b{AMOUNT_DONE money}_l:1_m:{AMOUNT money}_fullbar:&d{AMOUNT money}%&d/&d{AMOUNT money}`
#### Rankup's PAPI placeholder version
> `%progress_bar_{rankup_requirement_money_done}_p:&b{rankup_requirement_money_done}_l:1_m:{rankup_requirement_money}_fullbar:&d{rankup_requirement_money}%&d/&d%rankup_requirement_money%`
#### Note: these two placeholders above will work identically. The only difference is that the PAPI version can be used outside of a Rankup context, like a scoreboard. Does not include MVdW placeholders, click [here](../Core-Files/PAPI-Placeholders.md#mvdw-placeholders) to find out how to adapt the current placeholder to work with MVdW.

### What you need to change when you want to...
**important:  Look for the `>>> <<<`. If you copy paste the following placeholders, be sure to remove the `>>> <<<`.**
#### Change the amount of the requirement.
> Change the requirement itself. The placeholders will adapt to the changes without you needing to change the actual placeholder.
#### Change the requirement itself.
###### Config placeholder version
> `%progress_bar_{AMOUNT_DONE >>>money<<<}_p:&b{AMOUNT_DONE >>>money<<<}_l:1_m:{AMOUNT >>>money<<<}_fullbar:&d{AMOUNT >>>money<<<}%&d/&d{AMOUNT >>>money<<<}`
###### PAPI placeholder verion
> `%progress_bar_{rankup_requirement_>>>money<<<_done}_p:&b{rankup_requirement_>>>money<<<_done}_l:1_m:{rankup_requirement_>>>money<<<}_fullbar:&d{rankup_requirement_>>>money<<<}%&d/&d%rankup_requirement_>>>money<<<%`
#### Change the colors of the text.
> change the following in the placeholder itself
##### 1. Change the color the text turns to when the amount required is reached.
> `%progress_bar_{AMOUNT_DONE money}_p:&b{AMOUNT_DONE money}l:1_m:{AMOUNT money}_fullbar:>>>&d<<<{AMOUNT money}%&d/&d{AMOUNT money}`
##### 2. Change the color the text is when the amount required hasn't been reached yet.
> `%progress_bar_{AMOUNT_DONE money}_p:>>>&b<<<{AMOUNT_DONE money}_l:1_m:{AMOUNT money}_fullbar:&d{AMOUNT money}%&d/&d{AMOUNT money}`
##### 3. Change the color of the `total` in `X/total`.
> `%progress_bar_{AMOUNT_DONE money}_p:&b{AMOUNT_DONE money}_l:1_m:{AMOUNT money}_fullbar:&d{AMOUNT money}%&d/>>>&d<<<{AMOUNT money}`
##### 4. Change the color of the `/` in `X/total`.
> `%progress_bar_{AMOUNT_DONE money}_p:&b{AMOUNT_DONE money}_l:1_m:{AMOUNT money}_fullbar:&d{AMOUNT money}%>>>&d<<</&d{AMOUNT money}`
