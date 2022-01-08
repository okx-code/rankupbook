<html>
  <head>
    <meta name="description" content="Tutorial on managing players in dual group settings.">
    <meta name="keywords" content="Rankup, Minecraft, Plugin, Spigot, Prestige">
  </head>
</html>

# Dual-Track-Setup
> This tutorial is for advanced users only.  

You've got your ranks, prestiges, and are able to rankup in testing but need to manage your players using distinct rank AND prestige permission groups.  
You can already do this by adding [`commands:`](../Rankups-and-Prestiges/How-to-Rankups.yml.md#1-commands) from your permission plugin to manage players' groups/nodes.  
Instead, this tutorial is dedicated to a Rankup-only solution (__without__ `commands:`).  
#### When [`permission-rankup: true`](../GitHub/Rankup3/config/Permission-Rankup.html) this tutorial is irrelevant since Manual Mode expects `commands:` will change a player's permissions!
### Relevant Necessary Information to Understand This Tutorial
1. [heading](../Rankups-and-Prestiges/How-to-Rankups.yml.md#1-heading)
2. [from](../Rankups-and-Prestiges/How-to-Prestiges.yml.md#on-from-and-to)
3. [to](../Rankups-and-Prestiges/How-to-Prestiges.yml.md#on-from-and-to)
4. [next](../Rankups-and-Prestiges/How-to-Rankups.yml.md#3-next)
### Making A Zero Prestige to Escape from Rankless without `commands:`
If your prefixes, permissions, or another plugin setup requires players to have two groups simultaneously, this method gives players two starting groups without `commands:` or inefficient plugins like LuckPerms' [default assignments extension](../LuckPerms/Wiki/Default-Assignments-Extension.html) [(see also this page for reasons why not to use it)](../LuckPerms/Wiki/Default-Groups/Default-Assignments.html).  
The zero-ith or first prestige is different from any rankup or latter prestiges because it _requires only 1 permission group_ (`from:`) but _adds 2 groups_ (`to:` and `next:`) without `commands:`.
###### Commandless Escape From Rankless Example:
```yaml
Commandless-escapeFrom-Rankless: # first prestige in prestiges.yml
  from: 'default'   # for truly NO requirements
  to: 'rank0'       # you could replace the
  next: 'prestige0' # subsequent lines (5-6)
  requirements:     # with "requirements: []"
    - 'playtime-minutes 2'
```
`default` is a LuckPerms built-in but also represents the group that all players should start with.  
`rank0` and `prestige0` are placeholders for the groups you want players to have in your permission plugin.  
tldr: players will `/prestige` onto the Rankup **and** Prestige ladders *simultaneously* with this setup, which is literally the escape from Rankless.  
##### Commandless Escape From Rankless In Action
If you have rules or a terms of service or any other kind of introductory requirements for players joining your server, this option is especially useful in combination with an alias for `/prestige`, like `/iagree`, `/yestorules`, etc. By requiring a user to take the 0th prestige in order to get a permission group, you can setup a system to require new players to `/agree` to the server's rules and click an item in the confirmation `gui:` before, building, leaving a spawn region defined in worldguard, or generally progressing through any other plugin with permissions.  
In the example, I used `- 'playtime-minutes 2'` to prevent bots by requiring an amount of time before running the command on the server.  
It also _makes_ time for players to actually read the rules.  
