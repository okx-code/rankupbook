# How To `Rankups`  
## Each `heading:` in rankups.yml defines a Rankup from the current `rank:` group to the `next:` group which has some `requirements:`.  
### These are the **4 required sections** in the rankups.yml file necessary for a Rankup to be considered valid individually.  
### 1. `heading:`
Since you must name each heading to start a new rankup/prestige this is required.  
The heading or "the name of the configuration section" is considered `completely unused` because it is never seen reproduced in any message text unless it's a console error. What you name the step is unimportant as long as it's unique from every other heading. If two headings have the same name, which one is selected may vary randomly.
It holds **all** of the subsections of each distinct rankup/prestige.  
**An important note**: it can be named anything, not just "heading".  
Examples throughout the wiki will change the name of this heading.  
### 2. `rank:`
`rank:` defines the permission group a player must currently have to access this rankup, is mandatory in all Rankups **and Prestiges** except for the first prestige, and provides the placeholder `{OLD_RANK}`.
### 3. `next:`
`next:` defines the permission group a player will move to after completing the rankup, is mandatory in all Rankups **and Prestiges**, and provides the placeholder `{RANK}`.

The permission groups specified in `rank:` and `next:` should all use the name of the groups provided to Vault by your permission manager. For example, in LuckPerms the `'<name>'` of the group's `displayname.<name>` should be used in place of its internal name unless the display name/node isn't present.  
Do **NOT** `rank: 'displayname.<name>'`. Use `rank: '<name>'` exactly (case-sensitive) instead of the group's name (like the luckperms `default` group). This means they should be text (alpha-numeric with no special symbols nor unicode). 

If you are using [`permission-rankup: true`](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml#L41-L47) you should still avoid special symbols and/or unicode in these fields, as they may interfere with other plugins using vault.
### 4. `requirements:`
The `requirements:` section defines a list of required parameters the player needs to satify in order to move up the ladder (Rankup or Prestige) from *rank* to *next*.  
The list of requirements can be disabled with `requirements: []`.  
A requirement in the list can be any one or more from [The List of Requirements](https://github.com/okx-code/Rankup3/wiki/List-of-Requirements).  
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
### 1. `commands:`
`commands:` follows the format of `requirements:`. Each command listed is executed in-order after successfully meeting the requirements, executing `/rankup`, and [confirming the rankup](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml#L51). Commands do not require a preceding `/` to execute. `commands:` is also available in Prestiges.  
```yaml
CommandsExample: # "heading:"
  rank: 'A'
  next: 'B'
  requirements:
    - 'player-kills 1'
  commands:
    - 'say {PLAYER} ranked up to {RANK} at %world_time_world% in world: %world_name_world%' # requires PAPI and /papi ecloud download world
    - 'execute at {PLAYER} run playsound minecraft:ui.toast.challenge_complete player {PLAYER} ~ ~ ~' # plays a sound for the player
    - 'execute at {PLAYER} run particle minecraft:firework ~ ~1 ~ 1 1 1 0 30 normal' # makes a firework particle cloud on the player
    - 'title {PLAYER} subtitle {"text":"Congratulations!","bold":true,"color":"aqua"}' # adds a subtitle to the player's screen
    - 'title {PLAYER} title {"text":"Rankup'd!","bold":true,"color":"light_purple"}' # adds a title to the player's screen
```  
You may define as many commands as you like in the list. They support ***all [config placeholders](https://github.com/okx-code/Rankup3/wiki/Config-Placeholders) and [PlaceholderAPI placeholders](https://github.com/PlaceholderAPI/PlaceholderAPI/wiki/Placeholders)*** as well.
### 2. `display-name:`
You may have named your ranks exactly how you wanted them, but been unable to apply formatting or color codes directly to your `rank:` or `next:`.  
The rankup `display-name:` feature is where you can do so and is recommended for providing a unique appearance to ranks, separate from your group/permission manager. This feature does not require a toggle in the configuration to be activated. Instead, you may simply add `display-name:` to your rankups in the rankups.yml. This feature is also available for prestiges!
 
`display-name:` provides the `{RANK_NAME}` and `{OLD_RANK_NAME}`. This is similar to `rank:` but the placeholders `{RANK}` and `{OLD_RANK}` are distinct from the prior.  

`display-name:` more specifically provides the `{OLD_RANK_NAME}` placeholder to **the current `rank:`** while `{RANK_NAME}` gets the `next:` **rankup's** `display-name:`.  
If either `{OLD_RANK_NAME}` or `{RANK_NAME}` cannot find a `display-name:` the values from their non-`_NAME` variants will appear instead.  

Your last rankup, however, will need a display-name [saved in the configuration file](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml#L96) since it will never have a `next:` rankup to get a `display-name:` from.     
```yaml
DisplayNameExample:
  rank: 'A'
  next: 'B'
  display-name: '&2A&r is &4Boring'
  requirements: []
```

### 3. `rankup:`  
`rankup:` This section follows the same structure of the section by the same name in the locale and allows you to create custom messages for each rankup separate from the locale. All message fields accept [config placeholders](https://github.com/okx-code/Rankup3/wiki/Config-Placeholders) and all [PlaceholderAPI placeholders](https://github.com/PlaceholderAPI/PlaceholderAPI/wiki/Placeholders)! `rankup:` is not available in prestiges [(see below)](#message-me).  
```yaml
member:
  rank: 'guest'
  next: 'member'
  requirements:
    - 'money 10000'
  rankup:
    requirements-not-met: "&cYou need ${MONEY_NEEDED} more money to rankup."
```

# How to `Prestiges`
## Each `heading:` in prestiges.yml defines a Prestige from the current `rank:` group to the `next:` group, transitionary `from:` group `to:` group sections, and some `requirements:`.  
### Prestiges [when enabled in config.yml](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml#L27-L35) are similar to Rankups but require 1 to 2 more headings than [the minimal Rankup example](#an-example-of-the-minimum-required-fields-with-a-default-configyml-and-non-empty-requirements).  
###### Unlike Ranks, Prestiges do not currently support the GUI list features.
## On `from:` and `to:`  
If you have group-based rankup disabled ([`permission-rankup: true`](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml#L41-L47)), these options are not mandatory and will do nothing if used.  
The `from:` and `to:` sections are only used in prestiges.  
`from:` defines the group on the Rankup ladder a player needs to prestige at.  
`to:` defines the group on the Rankup ladder a player is moved to on completion.  
The permission groups specified in `to:` and `from:` should all use the name of the groups provided to Vault by your permission manager. For example, in LuckPerms the `<name>` of the group's `displayname.<name>` should be used in place of its internal name unless the display name/node isn't present.  
Do **NOT** `to: 'displayname.<name>'`. Use `to: '<name>'` exactly (case-sensitive) instead of the group's name (like the luckperms `default` group). This means they should be text (alpha-numeric with no special symbols nor unicode).
```yaml
first: # heading:
  from: 'B' # the required and removed on completion permission group
  to: 'A' # the assigned permission group (typically on the Rankup ladder)
  next: 'P1' # the assigned prestige permission group
  requirements: # same as in Rankups
    - 'money 10000'
```
In this example, when a player completes B rank, they will be able to /prestige to P1. If you are using group-based rankups ([`permission-rankup: false`](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml#L41-L47), they will be removed from group B (the `from:` group), and added to the group A (the `to:` group) and the P1 group (the `next:` group).
## Message Me!
Similar to customizing locale messages with `rankup:`, prestiges use the `prestige:` to customize messages per-prestige by following the same structure of the section by the same name in the locale. All message fields accept [config placeholders](https://github.com/okx-code/Rankup3/wiki/Config-Placeholders) and all [PlaceholderAPI](https://github.com/PlaceholderAPI/PlaceholderAPI/wiki/Placeholders) placeholders! `prestige:` is not available in rankups [(see above)](#3-rankup).

```yaml
prestige2: # heading:
  from: 'member'
  to: 'guest'
  rank: 'p1'
  next: 'p2'
  prestige:
    requirements-not-met: "&cYou need {MONEY} money to rankup."
```
# What's Special About Prestiges?  
## Prestige-Based Requirements  
### You can specify requirements by prestige in your rankups!  
For example, if you had ranks A and B, and the prestiges P1 and P2, you might have this in your rankups.yml:  
```yaml
a: # heading:
  rank: 'A'
  next: 'B'
  requirements:
    default: # used when a player hasn't prestiged
      - 'money 100'
    p1: # used in p1
      - 'money 200'
    p2: # used in p2
      - 'money 300'
```
When a player successfully ranks up from A to B, one of three things will happen:  
1. They will be charged $100 when they have not yet prestiged  
2. They will be charged $200 when they have prestiged to p1  
3. They will be charged $300 when they have prestiged to p2

This is the most significant difference between [`prestiges: false` and `prestiges: true`](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml#L41-L47)
