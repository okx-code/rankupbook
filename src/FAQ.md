<html>
  <head>
    <meta name="description" content="Responses to the most frequently asked questions.">
    <meta name="keywords" content="Rankup, Minecraft, Plugin, Spigot, Prestige, Installation">
  </head>
</html>

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
### Why Does `/rankup` say `You need <amnt> money to rankup.`
> You can read about why this message is displayed in [this section of the Configuration Example](./Basic-Configuration/Your-First-Rank.md).  
> You can read about how to change the message's contents in [this section of the Configuration Example](./Basic-Configuration/Wrong-Message.md).  
### How Does Rankup Handle Prefixes?
> Rankup does not manage prefixes! Consult your permission group and/or chat plugins.  
> If you followed this wiki's recommendation to use LuckPerms, you can learn about [Prefixes and Suffixes on the LuckPerms wiki!](./LuckPerms/Wiki/Prefix.html)  
> LuckPerms can also support multiple prefixes via [Prefix Stacking](./LuckPerms/Wiki/Stacking.html)  
### Where are a players' rankups stored in Rankup?
> Rankup doesn't save them!  
> Instead, your permission plugin stores a player's group information and provides it to Vault.  
> Rankup uses what's provided to Vault to place a player on the ladder if possible. (example: a player's primary-group in LuckPerms)  
### Do I need to add a command to manually change a player's group?
> No, Rankup automatically changes a player's groups when [`permission-rankup: false`](./GitHub/Rankup3/config/Permission-Rankup.html) (default).  
> [Learn about when and how to use `permission-rankup: true`.](./Advanced-Configuration/Permission-Rankup.md)  
### Does Rankup Clear Player's Other Permission Groups?
> No.  
> Rankup only applies/removes the groups specified in a rankup step written in your [rankups.yml](./GitHub/Rankup3/rankups.html) when [`permission-rankup: false`](./GitHub/Rankup3/config/Permission-Rankup.html) (default).  
> When [`permission-rankup: true`](./GitHub/Rankup3/config/Permission-Rankup.html), *you* change those groups manually.  
> See the [Permission Rankup](./Advanced-Configuration/Permission-Rankup.md) page for more information.  
### Why Does my Rank/Prestige not Change After `/rankup` or `/prestige`?
> This is a known issue if using GroupManager. GroupManager does not support Vault correctly, as it has not been updated since 1.7.  
> If you are on any permission manager not supported by Vault, like GroupManager or PermissionsEx, there are steps to [migrate to LuckPerms, the permissions plugin used in this wiki's example configurations](./LuckPerms/Wiki/Migration.html).  
> Otherwise, make sure the group you want to rankup to actually exists in your Vault-Compatible group management plugin.  
> Verify the group is named identically to the rankup step's [`rank:`](./GitHub/Rankup3/rankups/rank.html) and [`next:`](./GitHub/Rankup3/rankups/next.html) in your [rankups.yml](./GitHub/Rankup3/rankups.html).  
> If using `/prestige`, also verify prestiges have [been enabled in config.yml](./GitHub/Rankup3/config/Prestiges.html).  
### Why Aren't Placeholders Replaced in Messages From `/ranks`, `/rankup`, `/prestiges`, and `/prestige`?
> Try updating Rankup3! A new placeholder engine was added in version 3.12.  
> If your files use Old Placeholders, upgrade to their new Pebble Placeholder variants.  
> Though the [Old Placeholders](./Placeholders.md#Placeholders) remain supported, they offer fewer customization options.  
> We recommend using a 'find all and replace with' operation on each Old Placeholder for the new Pebble Placeholders.  
> You can find examples comparing the Pebble Placeholders and Old Placeholders [at the bottom of the Config Placeholders page.](./Placeholders.md#money-placeholders)  
### Why Don't Players Automatically Rankup When [`autorankup-interval:`](/GitHub/Rankup3/config/AutoRankup-Interval.html) is Non-Zero?
> Players also need the permission `rankup.auto`. Though [enabled by default](./GitHub/Rankup3/plugin/Auto-Rankup.html), you may have negated it.
### Does `/prestiges` Have a GUI Similar to `ranksgui:`?
> Though [`ranksgui:`](./GitHub/Rankup3/config/RanksGUI.html) is available in Rankup 3.10 or newer, `/prestiges` currently has no dedicated gui.
### When Executing `/rankup3 reload`, What Actually Gets Reloaded?
> Files like the `rankups.yml`, `prestiges.yml`, and selected locale are reloaded as described in the [Commands Reference](./Commands.html#admin-commands).  
> However, the reload command [executes the reload function](./GitHub/Rankup3/Java/commands/InfoCommand/reload.html) which only [reads all the prior listed files **and** `config.yml`](./GitHub/Rankup3/Java/Reload.html).
> The only contents of `config.yml` which *should* get repopulated during a reload at runtime are `autorankup-interval:` and `permission-rankup:`, but it's recommended to fully restart if changing *any* `config.yml` content.
# Error Questions
### A command replied <code class="hljs">An internal error occurred while attempting to perform this command</code>
> You should always **read the console** after a command fails **and** while starting your server.  
> This message is only used to indicate a problem. It provides no information intentionally.  
> Rankup will **NEVER** send detailed errors to *chat*.  
> Share only the errors from console in [discord](#discord-server-questions) when troubleshooting after receiving this message in chat.  
### Rankup3 Errors at Startup and `/rankup3 reload`! What's Wrong?
> Always execute `/rankup3 reload` from or while watching your server console.  
> This way you can see any error as it gets generated.  
> Read through the error's human readable text.  
> The plugin will often describe file parsing errors in the console by providing line and column numbers to the problem in your file.  
> You can also validate your yaml syntax with a validation service like **[CodeBeautify](./Validators/CodeBeautify.html)**.  
### Why Does `/rankup` say <code class="hljs">Sorry, but we could not find any rankups for the group(s) you are in. Use /ranks to list the rankups.</code>?
> The sender of `/rankup` does not belong to a permission group listed in your `rankups.yml`.  
> Fix your `rankups.yml` to utilize the correct group name or permission node or change the player's permission groups in your permission manager to match their actual progress on the rankup ladder.  
### <code class="hljs">Multiple root rankup nodes detected (a root rankup nodes is a rankup that does not have anything that ranks up to it). This may lead to inconsistent behaviour.</code>
> You can only have one rankup ladder!  
> Each rank at the bottom/beginning of a ladder is called a _"root"_ node. The root node indicates the start of a rankup ladder.  
> For each error listing a conflicting root node, you have `1 + error count` root nodes.  
> Fit unwanted root node back into the primary rankup ladder or remove the extraneous node and all rankup steps along its ladder of `next:` nodes if they exist.  
### <code class="hljs">[Server] INFO Caused by: java.lang.ArrayIndexOutOfBoundsException: Index (number) out of bounds for length (number)</code>
> If you see this line in your error, your GUI has been misconfigured.  
> Check that all fields of your `ranksgui:` and `gui:` are accurate and will [create a valid GUI](./Advanced-Configuration/RanksGUI.md#gui-sizing).  
# Requirement Questions
### How do I Convert `playtime-minutes` to Hours or Days?
> Use math operators in a pebble template to change the output of the placeholder.
### How do I use Data From Another Plugin as a Requirement?
> See the [custom requirements tutorial](./Advanced-Configuration/Adding-Custom-Requirements.md) or [developer page](./For-Developers.md).
# YAML Questions
### How should I make changes to the plugin files?
> Use a source code editor like Emacs/Vim/Atom/Sublime Text/Visual Studio Code/etc. when editing the files to "syntax highlight" or color the functional code.  
> You should edit the plugin's files in an editor with YAML syntax highlighting whenever possible.  
### Which Sections Provided in `rankups.yml` and/or `prestiges.yml` Should be Replaced/Removed?
> You must remove, replace, or integrate any functional code from the examples otherwise you may encounter unexpected results/errors.  
> Code following a "#" is known as a `comment`. _Comments_ are non-functional code which the plugin will ignore and are used to embed notes in the files.  
> You can safely ignore or remove the comments and refer to the **[rankups.yml](./GitHub/Rankup3/rankups.html)** file in this repository if you prefer.  
> Make sure to preserve the syntax of your own functional code when deleting large sections of the files.  
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
# Discord Server Questions
## How do I Share Information on the Discord Server?
> Discord can highlight your code when submitted as a file with the `.yml` extension or in a code block like the following:
````yaml
```yaml
code:
  rank: 'foo'
  next: 'bar'
  requirement: []
```
````
> Refrain from sharing large chunks of code using the above method.  
> Submitting a `.yml` file or pastebin link to your files is always preferred!  
> **Don't post images of files!**  
## Help! I was kicked from the [Discord Server](./Discord/Okx-Corner.html)!
> When you rejoin, make sure to read the #readme channel and pinned messages in the support channels **before asking or replying**.
## Help! I was banned from the [Discord Server](./Discord/Okx-Corner.html)!
> You can send Okx a spigot message to request an unban. Access is not guaranteed for those who violate the server's or Discord's rules.