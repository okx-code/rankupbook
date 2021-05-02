## Back to Basics
If you've followed the Configuration Example, you should now know how to make ranks and use the commands in Rankup3.
You should
1. Know the **[Sections](https://github.com/okx-code/Rankup3/wiki/How-to-rankups.yml-and-prestiges.yml)**
2. Have met **[The Basics](https://github.com/okx-code/Rankup3/wiki/Configuration-Example#the-basics)**
3. Know how **[To Format](https://github.com/okx-code/Rankup3/wiki/Configuration-Example#starting-to-format)**
4. Have made **[A Rankup](https://github.com/okx-code/Rankup3/wiki/Configuration-Example#your-first-rank)**
## What More?
Now that you know what is required for the plugin to work as intended, it's time to use the plugin to actually solve some problem for you;  
What do you want the plugin to actually do?  
This is the page where you'll find answers to specific questions about configuring ranks, prestiges, their text, and GUIs.

***

## How to implement CUSTOM requirements.

> Need more customization? If you can write Java, see [Developers](https://github.com/okx-code/Rankup3/wiki/Developers)

#### **IMPORTANT:** Make sure the plugin you want to use supports **PlaceholderAPI** (PAPI), if it doesn't you won't be able to use it.

First of all, you'll need a placeholder. It needs to output a **raw number**. That means that there can't be any periods/dots or comma's mixed in there.  
For example, if the placeholder outputs it like this it won't work:

`1000 = 1,000 or 1000.00`

Only __whole, unformatted numbers__ will work.

Now onto the syntax. This is the template:
###### Template
```yaml
RankName:
  rank: 'currentRank'
  next: 'nextRank'
  requirements:
    - 'placeholder <placeholder> <operation> <number>'
```
__Important things to note:__
- when using a placeholder, write `placeholder` in front of it so Rankup knows it's a placeholder.
- `<placeholder>` is where your placeholder goes. Again, unformatted numbers only.
- `<operation>` is where you specify what should be checked for. See below for a list of operations.
- `<number>` is the number that will be used by the `operation`.

### Operations
All of the following operations will be explained assuming the syntax above is used.

`>` greater than  
`<` smaller than  
`>=` equal to or greater than (**recommended**)  
`<=` smaller or equal to  
`=` equal to/matches  
`==` exact match (not recommended)  

##### An Example Operation:
```yaml
RankName:
  rank: 'currentRank'
  next: 'nextRank'
  requirements:
    - 'placeholder %statistic_hours_since_death% >= 5'
```
***
# Adding Lore to `ranksgui:`  
### 1. In the `locale`
Go to your **translation file** (`en.yml` by default) and scroll down to `line 41` and under each section (`complete`, `current` and `incomplete`) add under `name` **on the same level of indentation** the text `lore:`

It should look like this:
```yml
  ranksgui:
    title: "Ranks"
    rows: 3
    offset: 10
    width: 7
    complete:
      material: GREEN_STAINED_GLASS_PANE
      name: "&aRank &7{RANK} &a(completed)"
      lore: "Very Lore"
    current:
      material: ORANGE_STAINED_GLASS_PANE
      name: "&dRankup to &7{RANK}"
      lore: "Much\nLore"
    incomplete:
      material: RED_STAINED_GLASS_PANE
      name: "&cRank &7{RANK} &c(requires rankup)"
      lore: |-
        Wow
        Lore
    fill:
      material: BLACK_STAINED_GLASS_PANE
      name: ' '
```
### 2. In the `Rankups.yml`.
This is usually the preferred method but a bit more effort goes into it as well.

Go to your Rankups.yml, and add the following to __**each**__ rank:
```yaml
RankName:
  rank: 'currentRank'
  next: 'nextRank'
  requirements:
    - 'yourRequirementsHere'
  rankup: #start copying from this part! This note won't impact anything and can be removed. 
    ranksgui:
      title: "Ranks"
      rows: 3
      offset: 10
      width: 7
      complete:
        material: GREEN_STAINED_GLASS_PANE
        name: "&aRank &7{RANK} &a(completed)"
        lore: "Very Lore"
      current:
        material: ORANGE_STAINED_GLASS_PANE
        name: "&dRankup to &7{RANK}"
        lore: "Much\nLore"
      incomplete:
        material: RED_STAINED_GLASS_PANE
        name: "&cRank &7{RANK} &c(requires rankup)"
        lore: |-
          Wow
          Lore
      fill:
        material: BLACK_STAINED_GLASS_PANE
        name: ' '
```

### Customize your Ranksgui!
- Make `material` for `incomplete`, `current` and `complete` the same material but different for each rank so when you open the GUI each rank has its own item. materials must match the **[Spigot ENUM](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html)**

***
# Gui Offset Explanation  
![](https://i.imgur.com/rlLlcrp.png)  
`offset` increments the position ranks will begin at. The above image indicates what slot rankup will start from corresponding to the number you specify.  
`offset: 10`, for example, will make rankup start displaying ranks at the slot with 10 in the image above. Numbers outside the above range will cause errors.  
***
# Progress Bars
![](https://i.imgur.com/LcHp0Mx.png)

### Requirements:
- Have **[PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/)** installed.
- Have the **[Progress](https://github.com/PlaceholderAPI/PlaceholderAPI/wiki/Placeholders#progress)** extension installed.
***
#### I will not explain how to make your own progress bar. Instead, I will provide you with the link to the **[Progress wiki](https://github.com/aBooDyy/Progress-Expansion)** so you can learn to make your own.

## Installation Process.
#### 1. Install PlaceholderAPI (PAPI).
###### - **[PlaceholderAPI Spigot page](https://www.spigotmc.org/resources/placeholderapi.6245/)**.
#### 2. Install Progress extension.
###### - Execute `/papi ecloud download progress`.
#### 3. Reload PlaceholderAPI.
###### - Execute `/papi reload`.

### Important Notes:
- You can't use decimals.
- As long as you use percentages, the maximum should always be `100`.
- Placeholder (external) requirements require a different usage.
  - [Explanation.](https://github.com/okx-code/Rankup3/wiki/Advanced-Configuration-Example#progress-bars-with-placeholders)
- Rankup requirements that require sub-requirements will need their sub-requirements specified.
  - [Explanation.](https://github.com/okx-code/Rankup3/wiki/Advanced-Configuration-Example#progress-bars-with-sub-requirements)

##### The configuration below produced [the text in the first Progress Bar image](#progress-bars).
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
### If you use Rankup's [internal/config](https://github.com/okx-code/Rankup3/wiki/Config-Placeholders) placeholders, they won't work outside of any Rankup context, like a scoreboard or in tab. Use Rankup's [PAPI placeholders](https://github.com/okx-code/Rankup3/wiki/PAPI-Placeholders#config-papi-placeholders) for that instead.
#### Rankup's config placeholder version
> `%progress_bar_{PERCENT_DONE money}_c:&d|_p:&d|_r:&3|_l:20_m:100_fullbar:&a&lCompleted!%`
#### Rankup's PAPI placeholder version
> `%progress_bar_{rankup_requirement_money_percent_done}_c:&d|_p:&d|_r:&3|_l:20_m:100_fullbar:&a&lCompleted!%`
#### Note: these two placeholders above will work identically. The only difference is that the PAPI version can be used outside of a Rankup context, like a scoreboard. Does not include MVdW placeholders, click [here](https://github.com/okx-code/Rankup3/wiki/PAPI-Placeholders#mvdw-placeholders) to find out how to adapt the current placeholder to work with MVdW.

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
***
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
**Note: This placeholder uses the `money` requirement.** Here are the instructions to **[change it](https://github.com/okx-code/Rankup3/wiki/Advanced-Configuration-Example#change-the-requirement-itself)**.
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
### If you use Rankup's [internal/config](https://github.com/okx-code/Rankup3/wiki/Config-Placeholders) placeholders, they won't work outside of any Rankup context, like a scoreboard or in tab. Use Rankup's [PAPI placeholders](https://github.com/okx-code/Rankup3/wiki/PAPI-Placeholders#config-papi-placeholders) for that instead.
#### Rankup's config placeholder version
> `%progress_bar_{AMOUNT_DONE money}_p:&b{AMOUNT_DONE money}_l:1_m:{AMOUNT money}_fullbar:&d{AMOUNT money}%&d/&d{AMOUNT money}`
#### Rankup's PAPI placeholder version
> `%progress_bar_{rankup_requirement_money_done}_p:&b{rankup_requirement_money_done}_l:1_m:{rankup_requirement_money}_fullbar:&d{rankup_requirement_money}%&d/&d%rankup_requirement_money%`
#### Note: these two placeholders above will work identically. The only difference is that the PAPI version can be used outside of a Rankup context, like a scoreboard. Does not include MVdW placeholders, click [here](https://github.com/okx-code/Rankup3/wiki/PAPI-Placeholders#mvdw-placeholders) to find out how to adapt the current placeholder to work with MVdW.

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
*** 
## Who's that {RANK}!
###### This setup is extremely specific and for advanced users and niche scenarios only. When setup incorrectly, it may require manual correction of any affected users' groups.
You've got your ranks, prestiges, and are able to rankup in testing but need your players in distinct rank AND prestige permission groups. This section will detail exactly how to get rankless players not only into a rank, but also a prestige without `commands:`.
#### When you've configured [`permission-rankup: true`](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml#L41-L47), all of the `Commandless-escapeFrom-Rankless:` information is irrelevant as you **must** use `commands:` to change a player's permission groups.
### Relevant Necessary Information to Understand `Commandless-escapeFrom-Rankless:`
1. [heading](https://github.com/okx-code/Rankup3/wiki/How-to-rankups.yml-and-prestiges.yml#1-heading)
2. [from](https://github.com/okx-code/Rankup3/wiki/How-to-rankups.yml-and-prestiges.yml#on-from-and-to)
3. [to](https://github.com/okx-code/Rankup3/wiki/How-to-rankups.yml-and-prestiges.yml#on-from-and-to)
4. [next](https://github.com/okx-code/Rankup3/wiki/How-to-rankups.yml-and-prestiges.yml#3-next)
### Making A Zero Prestige to Escape from Rankless/Prestigeless without `commands:`
If your prefix, permissions, or another plugin setup requires your players to have multiple groups or be on several tracks at once in order to function optimally, this method will allow you to give players two starting groups without using `commands:` or inefficient plugins like LuckPerms' [default assignments extension](https://luckperms.net/wiki/Extensions#extension-default-assignments) [(see also this page for reasons why not to use it)](https://luckperms.net/wiki/Default-Groups#configure-default-assignments).  
The zero-ith or first prestige is different from any rankup or latter prestiges because it can assign two groups _**without the use of the**_ `commands:` section while requiring players have only 1 group. This tutorial is entirely dedicated to the importance of this distinction as it allows for unique, likely unintended, customization options. Using the lack of a `rank:` and the sole requirement being a single permission group `from:` your permission manager via Vault, you can create a system to grant 2 distinct permission groups in your Vault Compatible permission plugin of choice (like LuckPerms) without running permission plugin specific `commands:` to add them.
###### Commandless Escape From Rankless Example:
```yaml
Commandless-escapeFrom-Rankless: # in prestiges.yml
  from: 'default'   # for truly NO requirements
  to: 'rank0'       # you could replace the
  next: 'prestige0' # subsequent lines (5-6)
  requirements:     # with "requirements: []"
    - 'playtime-minutes 2'
```
`default` is a LuckPerms built-in but also represents the group that all players should start with.  
`rank0` and `prestige0` are placeholders for the groups you want players to have in your permission plugin.
##### Commandless Escape From Rankless In Action
If you have rules or a terms of service or any other kind of introductory requirements for players joining your server, this option is especially useful in combination with an alias for `/prestige`, like `/iagree`, `/yestorules`, etc. By requiring a user to take the 0th prestige in order to get a permission group, you can setup a system to require new players to `/agree` to the server's rules and click an item in the confirmation `gui:` before, for example building, leaving a spawn region defined in worldguard, or generally progressing through any other plugin with permissions.  
Ending this wall of text with a callback to the section's name: players will `/prestige` onto the Rankup **and** Prestige ladders *simultaneously* with this setup, which is literally the escape from Rankless.  
In the example, I used `- 'playtime-minutes 2'` to prevent bots by requiring an amount of time before running the command on the server.  
It also _makes_ time for players to actually read the rules.
*** 
# End-User Version Notes
#### Customizing your ranks and their appearance in-game has gotten refined and improved within Rankup3's ``/ranks`` interface options: Either Text Or GUI.
#### Since version 3.10, ranks can be displayed in an Inventory style GUI (previously only text and commands or text and confirmation GUI).  
#### Since version 3.11, ranks have optional ``display-name:`` overrides usable in both text and GUI interface options. 
##### Unlike Ranks, Prestiges do not currently support display-names or the GUI list features, though [display-name placeholders like `{RANK_NAME}` will use their described default value](https://github.com/okx-code/Rankup3/wiki/How-to-rankups.yml-and-prestiges.yml#2-display-name).
