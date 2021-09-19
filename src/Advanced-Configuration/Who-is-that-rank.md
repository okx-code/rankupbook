# Who's That {{rank}}!
> This setup is extremely specific and for advanced users and niche scenarios only. When setup incorrectly, it may require manual correction of any affected users' groups.
You've got your ranks, prestiges, and are able to rankup in testing but need your players in distinct rank AND prestige permission groups. This section will detail exactly how to get rankless players not only into a rank, but also a prestige without `commands:`.
#### When you've configured [`permission-rankup: true`](../GitHub/Rankup3/config/Permission-Rankup.html), all of the `Commandless-escapeFrom-Rankless:` information is irrelevant as you **must** use `commands:` to change a player's permission groups.
### Relevant Necessary Information to Understand `Commandless-escapeFrom-Rankless:`
1. [heading](../Rankups-and-Prestiges/How-to-Rankups.yml.md#1-heading)
2. [from](../Rankups-and-Prestiges/How-to-Prestiges.yml.md#on-from-and-to)
3. [to](../Rankups-and-Prestiges/How-to-Prestiges.yml.md#on-from-and-to)
4. [next](../Rankups-and-Prestiges/How-to-Rankups.yml.md#3-next)
### Making A Zero Prestige to Escape from Rankless/Prestigeless without `commands:`
If your prefix, permissions, or another plugin setup requires your players to have multiple groups or be on several tracks at once in order to function optimally, this method will allow you to give players two starting groups without using `commands:` or inefficient plugins like LuckPerms' [default assignments extension](../LuckPerms/Wiki/Default-Assignments-Extension.html) [(see also this page for reasons why not to use it)](../LuckPerms/Wiki/Default-Groups/Default-Assignments.html).  
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
