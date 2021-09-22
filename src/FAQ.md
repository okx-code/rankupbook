# Installation Questions
### What Rankup version do I need for Minecraft version 1.17/1.16/1.15/1.14/1.13/1.12/1.11/1.10/1.9/1.8/1.7?
> The latest Rankup version supports all Minecraft Spigot server versions. Only Minecraft Versions 1.13+ support all Rankup features.  
> An example of features that don't function in versions 1.12 or older includes any `requirements:` that check the Vanilla statistics menu since these are not available in 1.12 or lower due to [major changes](./Minecraft/Wiki/Flattening.html).  
> Rankup remained compatible with 1.15 and 1.16 on release and is expected to maintain compatibility with 1.17 when Spigot and other dependencies become available.  
> Always keep plugins like Rankup up-to-date.  
> Try to update to the latest version of Minecraft to maintain compatibility.
### What Servers Can I Use With Rankup?
> Rankup supports [Spigot](./Spigot/website.html) and [Paper](./GitHub/Paper/website.html). Ensure you are on the latest version before asking for support. CraftBukkit is known to not work with Rankup, and other forks are not guaranteed to be compatible.
### What should I save when migrating to a new host?
> When migrating, first you should make a copy of all the files in your `/plugins/rankup` directory to use on the new host.  
> Then use the migration information included with your permission plugin to maintain players' rankups on the new host.
# Starter Questions
### Where are a players' rankups stored in Rankup?
> Rankup doesn't save them! Instead, your permission plugin stores a player's group information and provides it to Vault.  
> Rankup uses what's provided to Vault to place a player on the ladder if possible. (example: a player's primary-group in LP)
### Do I need to add a command to manually change a player's group?
> No, Rankup automatically changes a player's groups when [`permission-rankup: false`](./GitHub/Rankup3/config/Permission-Rankup.html) (default).<br>
> [Learn about when and how to use `permission-rankup: true`.](./Advanced-Configuration/Permission-Rankup.md)
### Does Rankup clear a player's other groups?
> No. Rankup only changes the groups specified by the given rankup step in your [rankups.yml](./GitHub/Rankup3/rankups.html) when [`permission-rankup: false`](./GitHub/Rankup3/config/Permission-Rankup.html) (default).<br>When [`permission-rankup: true`](./GitHub/Rankup3/config/Permission-Rankup.html), *you* change those groups manually.<br>See the [Permission Rankup](./Advanced-Configuration/Permission-Rankup.md) page for more information.
### When I `/rankup` it still says `You need <amnt> money to rankup.`
> You can read about why this message is displayed in [this section of the Configuration Example](./Basic-Configuration/Your-First-Rank.md).  
> You can read about how to change the message's contents in [this section of the Configuration Example](./Basic-Configuration/Wrong-Message.md).
### I got an error at startup. What should I do?
> The plugin will often describe file parsing errors in the console by providing line and column numbers to the problem in your file.<br>You can also validate your yaml syntax with a validation service like **[CodeBeautify](./Validators/CodeBeautify.html)**.  
### When I `/rankup3 reload` the command fails. What do I do?
> Always execute `/rankup3 reload` from the console.<br>This way you can see any error as it gets generated.<br>Read through the error's human readable text.<br>It often contains a message describing the cause of the error in your file. <br>You should always **read the console** after a command fails.<br>Rankup will **NEVER** send detailed errors to *chat*.
### When I `/rankup` and/or `/prestige`, I don't get any rank or prestige. What do I do?
> This is a known issue if using GroupManager. GroupManager does not support Vault correctly, as it has not been updated since 1.7.  
> If you are on any permission manager not supported by Vault, like GroupManager or PermissionsEx, there are steps to [migrate to LuckPerms, the permissions plugin used in this wiki's example configurations](./LuckPerms/Wiki/Migration.html).  
### When I `/rankup` and/or `/prestige`, my rank/prestige doesn't change. What do I do?
> Make sure the group you want to rankup to actually exists in your Vault-Compatible group management plugin and has the same name.
> Otherwise, verify your groups are named identically to the rankup step's [`rank:`](./GitHub/Rankup3/rankups/rank.html) and [`next:`](./GitHub/Rankup3/rankups/next.html) in your [rankups.yml](./GitHub/Rankup3/rankups.html). If the error occurs with `/prestige`, also check that prestiges have [been enabled in config.yml](./GitHub/Rankup3/config/Prestiges.html).
### Why don't players automatically rankup when I have Auto-Rankup enabled?
> Players also need the permission rankup.auto. It's [enabled by default](./GitHub/Rankup3/plugin/Auto-Rankup.html) but you may have negated it.
### Can I have a GUI for `/prestiges`?
> Though [`ranksgui:`](./GitHub/Rankup3/config/RanksGUI.html) is available in Rankup 3.10 or newer, `/prestiges` do not have a dedicated gui.
### Why aren't my placeholders replaced when I /ranks or /prestiges?
> The [Old Config Placeholders](./Config-Placeholders.md#config-placeholders) are not supported beyond version 3.12. You must replace all of the old placeholders with their new variants. We recommend using a simple `find all and replace with` operation in notepad or your code editor of choice to continue using your files. You can find examples of the new placeholders on the [Config Placeholders](./Config-Placeholders.md#config-placeholders) page or in the [rankup3 repository on github](./GitHub/Rankup3/resources.html).
# Requirement Questions
### How do I Convert `playtime-minutes` to Hours or Days?
> Use math operators in a pebble template to change the output of the placeholder.
### How do I use Data From Another Plugin as a Requirement?
> See the [custom requirements tutorial](./Advanced-Configuration/Adding-Custom-Requirements.md) or [developer page](./For-Developers.md).
# YAML Questions
### How should I make changes to the plugin files?
> Use a text editor like Vim when editing the files to "syntax highlight" or colour the functional code. You should edit the plugin's files in a text editor with YAML syntax highlighting whenever possible.
### What sections of the provided rankups.yml or prestiges.yml should be replaced/removed?
> You should remove or replace any functional code from the examples.  
> Code following a "#" is known as a `comment`. _Comments_ are non-functional code which the plugin will ignore and are used to embed notes in the files.  
> You can safely remove the comments and refer to the **[rankups.yml](./GitHub/Rankup3/rankups.html)** file in this repository if you prefer. Make sure to preserve the syntax of the functional code when deleting large sections of the files.
### How do I write multi-line messages?

> [https://yaml-multiline.info/](./Validators/Multiline.html)
>
> tl;dr
> use either |- and newlines or double quotes and \n
##### Example Block Style with |-
```yaml
message: |-
  firstline
  secondline
```
> will appear in chat as  
```
firstline
secondline
```  
#### OR  
##### Example Double Quoted Style with \n  
```yaml
message: "firstline\nsecondline"
```
> will appear in chat as
```
firstline
secondline
```  
Of these two, the first is recommended by Okx.  
The other newline behavior options detailed in [https://yaml-multiline.info/](./Validators/Multiline.html) are not recommended for beginners and are not included in default configurations.
# [Discord Server](./Discord/Okx-Corner.html) Questions
## Help! I was kicked from the discord server!
> When you rejoin, make sure to read the #readme channel and pinned messages in the support channels **before asking or replying**.
## Help! I was banned from the discord server!
> You can send Okx a spigot message to request an unban. Access is not guaranteed for those who violate the server's or Discord's rules.