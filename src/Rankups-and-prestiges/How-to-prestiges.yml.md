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

This is the most significant difference between [prestiges: false and prestiges: true](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml#L41-L47)
---
# How to Prestiges
## Each heading: in prestiges.yml defines a Prestige from the current rank: group to the next: group, transitionary from: group to: group sections, and some requirements:.  
### Prestiges [when enabled in config.yml](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml#L27-L35) are similar to Rankups but require 1 to 2 more headings than the minimal Rankup example.  
###### Unlike Ranks, Prestiges do not currently support the GUI list features.
## On from: and to: 
If you have group-based rankup disabled ([permission-rankup: true](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml#L41-L47)), these options are not mandatory and will do nothing if used.  
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
Similar to customizing locale messages with `rankup:`, prestiges use the `prestige:` to customize messages per-prestige by following the same structure of the section by the same name in the locale. All message fields accept [config placeholders](../Core-Files/Config-Placeholders) and all [PlaceholderAPI](https://github.com/PlaceholderAPI/PlaceholderAPI/wiki/Placeholders) placeholders! `prestige:` is not available in rankups [(see above)](#3-rankup).

```yaml
prestige2: # heading:
  from: 'member'
  to: 'guest'
  rank: 'p1'
  next: 'p2'
  prestige:
    requirements-not-met: "&cYou need {MONEY} money to rankup."
```
