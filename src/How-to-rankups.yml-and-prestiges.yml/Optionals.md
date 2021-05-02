# Optionals
## You may also add the following sections to enable further features:
### 1. `commands:`
Compatability Chart:

rankups.yml | prestiges.yml
--- | ---
yes | yes

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
Compatability Chart:

rankups.yml | prestiges.yml
--- | ---
yes | no

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
Compatability Chart:

rankups.yml | prestiges.yml
--- | ---
yes | no

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

### 4. `prestige`
Compatability Chart:

rankups.yml | prestiges.yml
--- | ---
no | yes

`prestige:` is similar to `rankup` but for the `prestiges.yml` instead. You have around the same amount of customisability because the two sections share a lot of options. All messages in `prestige` support placeholders, both internal and PAPI placeholders.
```yaml
prestige1:
  next: 'P1'
  from: 'member'
  to: 'guest'
  requirements:
    - 'money 1000000'
  prestige:
    requirements-not-met: "You don't have enough money!"
```
