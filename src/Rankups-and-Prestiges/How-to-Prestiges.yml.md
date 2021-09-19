<html>
  <head>
    <meta name="description" content="Reference for Prestiges.yml including all mandatory and optional sections.">
    <meta name="keywords" content="Rankup, Minecraft, Plugin, Spigot, Optionals, Commands, Prestige, Displayname">
  </head>
</html>

# How to `Prestiges.yml`
## Each `heading:` in prestiges.yml defines a Prestige from the current `rank:` group to the `next:` group, transitionary `from:` group `to:` group sections, and some `requirements:`.  
### Prestiges [when enabled in config.yml](../GitHub/Rankup3/config/Prestige.html) are similar to Rankups but require 1 to 2 more headings than [the minimal Rankup example](./How-to-Rankups.yml.html#an-example-of-the-minimum-required-fields-with-a-default-configyml-and-non-empty-requirements).  
#### Unlike Ranks, Prestiges do not currently support the GUI list features.
## On `from:` and `to:`  
If you have group-based rankup disabled ([`permission-rankup: true`](../GitHub/Rankup3/config/Permission-Rankup.html)), these options are not mandatory and will do nothing if used.  
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
In this example, when a player completes B rank, they will be able to /prestige to P1. If you are using group-based rankups ([`permission-rankup: false`](../GitHub/Rankup3/config/Permission-Rankup.html), they will be removed from group B (the `from:` group), and added to the group A (the `to:` group) and the P1 group (the `next:` group).
## Message Me!
Similar to customizing locale messages with `rankup:`, prestiges use the `prestige:` to customize messages per-prestige by following the same structure of the section by the same name in the locale. All message fields accept [config placeholders](../Config-Placeholders.md) and all [PlaceholderAPI](../GitHub/PAPI/Placeholders.html) placeholders! `prestige:` is not available in rankups.

```yaml
prestige2: # heading:
  from: 'member'
  to: 'guest'
  rank: 'p1'
  next: 'p2'
  prestige:
    requirements-not-met: "&cYou need {{ rank.requirement('money').total | money }} money to rankup."
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

This is the most significant difference between [`prestiges: false` and `prestiges: true`](../GitHub/PAPI/Placeholders.html)

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
You may define as many commands as you like in the list. They support ***all [config placeholders](../Config-Placeholders.md) and [PlaceholderAPI placeholders](../GitHub/PAPI/Placeholders.html)*** as well.

### 2. prestige:
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
