<meta name="description" content="Reference for Rankups.yml including all mandatory and optional sections.">
<meta name="keywords" content="Rankup, Minecraft, Plugin, Spigot, Optionals, Commands, Prestige, Displayname, Color">
<div style="float: right">
    <h3>Table of Contents</h3>
    <a href="#1-heading">Heading</a><br>
    <a href="#2-rank-and-next">Rank and Next</a><br>
    <a href="#3-finding-group-names">Finding Group Names</a><br>
    <a href="#4-requirements">Requirements</a><br>
    <h4>Optionals</h4>
    <a href="#1-commands">Commands</a><br>
    <a href="#2-display-name">Display-Name</a><br>
    <a href="#3-rankup">Rankup</a><br>
  </div>

# How To `Rankups.yml`  
## Each `heading:` in rankups.yml defines a Rankup from the current `rank:` group to the `next:` group which has some `requirements:`.  
### These are the **4 required sections** in the rankups.yml file necessary for a Rankup to be considered valid individually.  
### 1. `heading:`
Each heading is "a name in the configuration section" and holds **all** of the subsections for each distinct rankup/prestige.  
Since you must name each step to start a new rankup/prestige, headings are required.  
However, the heading is considered `completely unused` because it is never seen reproduced in any message text unless it's a console error.  
The step's name is unimportant, but **must be unique from every other heading**. If two headings have the same name, only one is used, typically the first.  
**An important note**: headings may be named anything, not just "heading".  
Throughout the wiki various heading names are used for different examples.  
### 2. `rank:` and `next:`
`rank:` defines the permission group a player must currently have to access this rankup, is mandatory in all Rankups **and Prestiges** except for the first prestige, and provides the placeholder `{{ rank.rank }}`.
`next:` defines the permission group a player will move to after completing the rankup, is mandatory in all Rankups **and Prestiges**, and provides the placeholder `{{ next.rank }}`.
### 3. Finding Group Names
The permission groups specified in `rank:`, `next:`, [`to:` and `from:`](How-to-Prestiges.yml.html#on-from-and-to) should all use the name of the groups provided to Vault by your permission manager. For example, in LuckPerms the `'<name>'` of the group's `displayname.<name>` should be used in place of its internal name unless the display name/node isn't present.  
Do **NOT** `rank: 'displayname.<name>'`. Use `rank: '<name>'` exactly (case-sensitive) instead of the group's name (like the luckperms `default` group). This means they should be text (alpha-numeric with no special symbols nor unicode).  
If you are using [`permission-rankup: true`](../GitHub/Rankup3/config/Permission-Rankup.html) you should still avoid special symbols and/or unicode in these fields, as they may interfere with other plugins using vault.
### 4. `requirements:`
The `requirements:` section defines a list of required parameters the player needs to satify in order to move up the ladder (Rankup or Prestige) from *rank* to *next*.  
The list of requirements can be disabled with `requirements: []`.  
A requirement in the list can be any one or more from [The List of Requirements](../List-of-Requirements.md#list).  
#### An example of the minimum required fields with a default config.yml and non-empty requirements:
```yaml
# text following a "# " is a comment in yaml
heading: # "heading" is unused and could be named differently
  rank: first # the permission group required-to and removed-post completion
  next: last # the permission group assigned on completion
  requirements: # things other than `rank:` required for completion
    - 'money 0' # any requirement
```
Requirements are in the format `'requirement-name value'`.  
Some requirements support sub-requirements, and can be used like `requirement-name sub-requirement value`.  
For example: `'mob-kills skeleton 100'`.  

Requirements may also be deductible, which means the player's parameters will be deducted upon completion.  
All payable/deductible requirements may be made non-deductible by adding the letter *h* to the end of the requirement name.  
For example: `money` deducts the subsequent amount while `moneyh` only checks the requirement was met.

# Optionals
## You may also add the following sections to enable further features:
### 1. commands:
`commands:` follows the format of `requirements:`. Each command listed is executed in-order after successfully meeting the requirements, executing `/rankup`, and [confirming the rankup](../GitHub/Rankup3/config/ConfirmationGUI.html). Commands do not require a preceding `/` to execute. 
```yaml
CommandsExample: # "heading:"
  rank: 'A'
  next: 'B'
  requirements:
    - 'player-kills 1'
  commands:
    - 'say {{player}} ranked up to {{next.rank}} at %world_time_world% in world: %world_name_world%' # requires PAPI and /papi ecloud download world
    - 'execute at {{player}} run playsound minecraft:ui.toast.challenge_complete player {{player}} ~ ~ ~' # plays a sound for the player
    - 'execute at {{player}} run particle minecraft:firework ~ ~1 ~ 1 1 1 0 30 normal' # makes a firework particle cloud on the player
    - 'title {{player}} subtitle {"text":"Congratulations!","bold":true,"color":"aqua"}' # adds a subtitle to the player's screen
    - 'title {{player}} title {"text":"Rankup!","bold":true,"color":"light_purple"}' # adds a title to the player's screen
```  
You may define as many commands as you like in the list. They support ***all [Placeholders](../Placeholders.md) including [PlaceholderAPI placeholders](../GitHub/PAPI/Placeholders.html)***.

### 2. display-name:
You may have named your ranks exactly how you wanted them, but been unable to apply formatting or color codes directly to your `rank:` or `next:`.  
The rankup `display-name:` feature is where you can do so and is recommended for providing a unique appearance to ranks, separate from your group/permission manager. This feature does not require a toggle in the configuration to be activated. Instead, you may simply add `display-name:` to your rankups in the rankups.yml.
 
`display-name:` provides the `{{next.name}}` and `{{rank.name}}`. This is similar to `rank:` but the placeholders `{{next.rank}}` and `{{rank.rank}}` are distinct from the prior.  

`display-name:` more specifically provides the `{{rank.name}}` placeholder to **the current `rank:`** while `{{next.name}}` gets the `next:` **rankup's** `display-name:`.  
If either `{{rank.name}}` or `{{next.name}}` cannot find a `display-name:` the values from their non-`.name` variants will appear instead.

Your last rankup, however, will need a display-name [saved in the configuration file](../GitHub/Rankup3/config/DisplayName.html) since it will never have a `next:` rankup to get a `display-name:` from.     
```yaml
DisplayNameExample:
  rank: 'A'
  next: 'B'
  display-name: '&2A&r is &4Boring'
  requirements: []
```

#### 2.1 Color Codes:
Rankup supports RGB color codes like `&#hexnum` in 1.16+.  
Otherwise, use old native codes [(`§4` or `&4`)](../Minecraft/Wiki/Color-Codes.html) or [bukkit codes (`§x§9§D§6§5§F§F`)](../Spigot/Docs/chat-color.html).

### 3. `rankup:`
`rankup:` This section follows the same structure of the section by the same name in the locale and allows you to create custom messages for each rankup separate from the locale. All message fields accept all [Placeholders](../Placeholders.md) including all [PlaceholderAPI placeholders](../GitHub/PAPI/Placeholders.html)! The `rankup:` keyword is not available in `prestiges.yml`. Use [`prestige:`](./How-to-prestiges.yml.md#2-prestige) instead.  
```yaml
member:
  rank: 'guest'
  next: 'member'
  requirements:
    - 'money 10000'
  rankup:
    requirements-not-met: "&cYou need ${{ rank.requirement('money').remaining | money }} more money to rankup."
```
