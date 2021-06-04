### What Rankup version do I need for Minecraft version 1.16/1.15/1.14/1.13/1.12/1.11/1.10/1.9/1.8/1.7?
> The latest Rankup version supports all Minecraft Spigot server versions. Only Minecraft Versions 1.13+ support all Rankup features. Rankup remained compatible with 1.15 and 1.16 on release and is expected to maintain compatibility with 1.17 when Spigot and other dependencies become available. Always keep plugins like Rankup up-to-date.
### Where should I start using this plugin?
> Review the [YAML Questions](#YAML-Questions) and then [follow the step by step configuration example!](../Basic-Configuration-Example/Your-first-rank.md)
### What Servers Can I Use With Rankup?
> Do not use CraftBukkit with Rankup. Rankup is made by Okx specifically for [Spigot](https://www.spigotmc.org/). The popular Spigot fork [Paper](https://papermc.io/) is _usually_ compatible. [Tuinity](https://github.com/Spottedleaf/Tuinity) and other forks are not recommended due to the volatility of rolling release server patchers. That's not an insult to server patchers or their authors, it's simply a byproduct of that release model. Though Rankup _may_ operate on rolling release server patchers, they are too numerous to test individually for real-time compatibility. Only Spigot is guaranteed by Okx. Paper is _expected_, **not guaranteed**. If your files are 100% valid but the plugin encounters errors or has unusual behavior while running on a server other than Spigot or Paper, you should revert to Spigot and test your files. Always keep your server up-to-date, but especially so when running Paper or another rolling release server patcher.
### Where can I find the latest default files for updating?
> [You can see the default config here.](https://github.com/okx-code/Rankup3/tree/master/src/main/resources)
### Where are a players' rankups stored in Rankup?
> Rankup doesn't save them! Instead, your permission plugin stores a player's group information and provides it to Vault.  
> Rankup uses what's provided to Vault to place a player on the ladder if possible. (example: a player's primary-group in LP)
### What should I save when migrating to a new host?
> When migrating, first you should make a copy of all the files in your `/plugins/rankup` directory to use on the new host.  
> Then use the migration information included with your permission plugin to maintain players' rankups on the new host.
### When I /rankup it still says `You need {{ rank.requirement('money').total | money }} money to rankup.`
> You can read about why this message is displayed in [this section of the Configuration Example](../Basic-Configuration-Example/Your-first-rank.md).  
> You can read about how to change the message's contents in [this section of the Configuration Example](../Basic-Configuration-Example#Wrong-message.md).
### Do I need to add a command to manually change a player's group?
> No, Rankup automatically changes a player's groups when [`permission-rankup: false`](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml#L41-L47) (default).
### Does this clear a player's other groups or just change their rankup group?
> Rankup only changes the groups specified by the given rankup step in your [rankups.yml](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/rankups.yml) when [`permission-rankup: false`](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml#L41-L47) (default).
### When I /rankup and/or /prestige, I don't get any rank or prestige. What do I do?
> This is a known issue if using GroupManager. GroupManager does not support Vault correctly, as it has not been updated since 1.7.  
> If you are on any permission manager not supported by Vault, like GroupManager or PermissionsEx, there are steps to [migrate to LuckPerms, the permissions plugin used in this wiki's example configurations, here](https://luckperms.net/wiki/Migration).  
### When I /rankup and/or /prestige, my rank/prestige doesn't change. What do I do?
> Make sure the group you want to rankup to actually exists in your Vault-Compatible group management plugin and has the same name.
> Otherwise, verify your groups are named identically to the rankup step's [`rank:`](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/rankups.yml#L12) and [`next:`](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/rankups.yml#L14) in your [rankups.yml](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/rankups.yml). If the error occurs with `/prestige`, also check that prestiges have [been enabled in config.yml](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml#L21).
### Why don't players automatically rankup when I have Auto-Rankup enabled?
> Auto-rankup needs the permission rankup.auto. It's provided by default but you may have negated it.
### I'm getting a PlaceholderAPI error:
> `Caused by: java.lang.ClassNotFoundException: me.clip.placeholderapi.PlaceholderAPI`
Update your version of Rankup.
### Can I have a GUI for `/ranks`?
> Yes, [`ranksgui:`](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml#L23-L25) is available in Rankup 3.10 or newer. `/prestiges` do not have a dedicated gui. However, both Ranks and Prestiges can use the [ConfirmationGUI](../Basic-Configuration-Example/Confirmation-gui) when [enabled](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml#L49-L51).
# YAML Questions
### How should I make changes to the plugin files?
> Use a source code editor like Sublime Text, Notepad++, Visual Studio, IntelliJ IDEA, Emacs, Vim, etc. when editing the files to "syntax highlight" or color the functional code. You should edit the plugin's files in a code editor with YAML syntax highlighting whenever possible.
### What sections of the provided rankups.yml or prestiges.yml should be replaced/removed?
> You should remove or replace any functional code from the examples.  
> Code following a "#" is known as a `comment`. _Comments_ are non-functional code which the plugin will ignore and are used to embed notes in the files.  
> You can safely remove the comments and refer to the **[rankups.yml](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/rankups.yml)** file in this repository if you prefer. Make sure to preserve the syntax of the functional code when deleting large sections of the files.
### I got an error at startup or when reloading the plugin, what should I do?
> Validate your code's syntax before, during, and after making changes. **[CodeBeautify](https://codebeautify.org/yaml-validator)** provides a syntax validation service.  
> If validation online is unavailable or you are unwilling to rely on another service, then the plugin will often describe file parsing errors in the console by providing line and column numbers to the problem. You can always read the console after running commands that fail or utilize the Rankup **[Discord Server](https://discord.gg/zbkbhBj)** if you have purchased the plugin.
### How do I write multi-line messages?

> https://yaml-multiline.info/
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
The other newline behavior options detailed in https://yaml-multiline.info/ are not recommended for beginners and are not included in default configurations.
