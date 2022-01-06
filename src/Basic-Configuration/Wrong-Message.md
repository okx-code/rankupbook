<html>
  <head>
    <meta name="description" content="Introduction to customizing rankup's messages!">
    <meta name="keywords" content="Rankup, Minecraft, Plugin, Spigot, Prestige">
  </head>
</html>

# Wrong Message
### You have 2 options to change messages:
1. Add a section to each rankup overriding the messages from the locale to display the correct text. This is the method recommended by the plugin's author Okx.  
2. Edit the `locale` for your language of choice. We will be using `plugins/rankup/locale/en.yml`. Editing the locale requires significantly more planning as these messages may affect **all rankup steps** unless overridden by option 1.  
###### These options also apply to prestiges in prestiges.yml
### Option 1:  
```yaml
rankup:
    requirements-not-met: "&cYou have {{ rank.requirement('xp-level').progress | simple }}, and need {{ rank.requirement('xp-level').total | simple }} xp levels to rankup!"
```
Add the section above to the rankup step in rankups.yml and be sure to properly _indent it_ (2 spaces). This option enables per rank message customization using an identical format to the structure provided in the `locale`. You can customize the messages from the locale by copying those lines into your rankups in rankups.yml, making sure to use the identical structure found in your locale or [the default locale file](../GitHub/Rankup3/locale.html) and **properly _indenting_**. Continuing our example, after you've pasted the provided message into `rankups.yml` your rankup step should look like this:  
```yaml
beginner:
  rank: 'default'
  next: 'member'
  requirements:
    - xp-level 5
  rankup:
    requirements-not-met: "&cYou have {{ rank.requirement('xp-level').progress | simple }}, and need {{ rank.requirement('xp-level').total | simple }} xp levels to rankup!"
```  
Let's analyze the last 2 lines:  
1. [`rankup:`](../Rankups-and-Prestiges/How-to-Rankups.yml.html#3-rankup) tells Rankup which section of the locale's messages we are overwriting for this step. The path used to overwrite custom messages in rankups **must** follow the same subsection construction as in our locale file. For example, changing the prestiges' messages requires [`prestige:`](../Rankups-and-Prestiges/How-to-Prestiges.yml.md#message-me) instead of `rankup:`.  
2. `requirements-not-met: <text>` is the message we're overwriting from the `locale`. Properly _indent_ overwritten messages as well.
### Option 2:  
[Open the `locale` folder and open your language of choice](../GitHub/Rankup3/locale.html), in our case [`en.yml`](../GitHub/Rankup3/locale/en.html).  
At the very top of the file, you can see the message we just received in chat: `requirements-not-met: "You need {{ rank.requirement('money').total | money }} money to rankup."`. Changing the `{{ rank.requirement('money').total | money }}` part to `{{ rank.requirement('<requirement>').total | simple }}`, with `<requirement>` in our case being `xp-level`, will "fix" the problem.  
Try changing the message like this:
```yaml
requirements-not-met: "&cThis rank requires {{ rank.requirement('xp-level').total | simple }} xp levels. You have {{ rank.requirement('xp-level').progress | simple }}, and need {{ rank.requirement('xp-level').remaining | simple }} xp levels!"
```
Let's review the message on a per-placeholder basis this time:
* `{{ rank.requirement('xp-level').total | simple }}` is the placeholder for how many levels the rankup step requires, as defined in the rankup step's `requirements:` section.
* `{{ rank.requirement('xp-level').progress | simple }}` is the placeholder for how many levels the player _already has_.
* `{{ rank.requirement('xp-level').remaining | simple }}` is the placeholder for how many levels the player _needs_.
A **[List of Requirements](../List-of-Requirements.md)** and **[Placeholders](../Placeholders.md)** will be useful for creating your ranks' requirements and messages.  

This method allows for modification of canned (default) messages.  
### Post-Options
Now that you've implemented **one or both of the options, let's try the new message! Assuming you have 0 xp, it will look like this:
```
You have 0, and need 5 xp levels to rankup!
```
That looks much better! Now let's try again with 5 xp levels.  
**NOTE:** if using @p in the below command returns "Error: player not found.", use your username instead.
```
/xp set @p 5 levels
/rankup
```
You should either successfully rankup, be required to type to confirm then rankup, or move to the next section about the Confirmation GUI.  
If you don't [enable the Confirmation GUI](../GitHub/Rankup3/config/ConfirmationGUI.html) the next section is not applicable.
