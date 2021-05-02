# Wrong Message
### You have 2 options to change messages:
1. Add a section to each rankup overriding the messages from the locale to display the correct text. This is the method recommended by the plugin's author Okx.  
2. Edit the `locale` for your language of choice. We will be using `plugins/rankup/locale/en.yml`. Editing the locale requires significantly more planning as these messages may affect **all rankup steps** unless overridden by option 1.  
###### These options also apply to prestiges in prestiges.yml
### Option 1:  
```yaml
rankup:
    requirements-not-met: "&cYou have {AMOUNT_DONE xp-level}, and need {AMOUNT xp-level} xp levels to rankup!"
```
Add the section above to the rankup step in rankups.yml and be sure to properly _indent it_ (2 spaces). This option enables per rank message customization using an identical format to the structure provided in the `locale`. You can customize the messages from the locale by copying those lines into your rankups in rankups.yml, making sure to use the identical structure found in your locale or [the default locale file](https://github.com/okx-code/Rankup3/tree/master/src/main/resources/locale) and **properly _indenting_**. Continuing our example, after you've pasted the provided message into `rankups.yml` your rankup step should look like this:  
```yaml
beginner:
  rank: 'default'
  next: 'member'
  requirements:
    - xp-level 5
  rankup:
    requirements-not-met: "&cYou have {AMOUNT_DONE xp-level}, and need {AMOUNT xp-level} xp levels to rankup!"
```  
Let's analyze the last 2 lines:  
1. [`rankup:`](https://github.com/okx-code/Rankup3/wiki/How-to-rankups.yml-and-prestiges.yml#3-rankup) tells Rankup which section of the locale's messages we are overwriting for this step. The path used to overwrite custom messages in rankups **must** follow the same subsection construction as in our locale file. For example, changing the prestiges' messages requires [`prestige:`](https://github.com/okx-code/Rankup3/wiki/How-to-rankups.yml-and-prestiges.yml#message-me) instead of `rankup:`.  
2. `requirements-not-met: <text>` is the message we're overwriting from the `locale`. Properly _indent_ overwritten messages as well.
### Option 2:  
[Open the `locale` folder and open your language of choice](https://github.com/okx-code/Rankup3/tree/master/src/main/resources/locale), in our case [`en.yml`](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/locale/en.yml).  
At the very top of the file, you can see the message we just received in chat: `requirements-not-met: "You need {MONEY} money to rankup."`. Changing the `{MONEY}` part to `{AMOUNT <requirement>}`, or in our case `xp-level`, will "fix" the problem.  
Try changing the message like this:
```yaml
requirements-not-met: "&cThis rank requires {AMOUNT xp-level} xp levels. You have {AMOUNT_DONE xp-level}, and need {AMOUNT_NEEDED xp-level} xp levels!"
```
Let's review the message on a per-placeholder basis this time:
* `{AMOUNT xp-level}` is the placeholder for how many levels the rankup step requires, as defined in the rankup step's `requirements:` section.
* `{AMOUNT_DONE xp-level}` is the placeholder for how many levels the player _already has_.
* `{AMOUNT_NEEDED xp-level}` is the placeholder for how many levels the player _needs_.
A **[List of Requirements](https://github.com/okx-code/Rankup3/wiki/List-of-Requirements)** and **[Config Placeholders](https://github.com/okx-code/Rankup3/wiki/Config-Placeholders)** will be useful for creating your ranks' requirements and messages.  

This method allows for modification of canned (default) messages.  
### Post-Options
Now that you've implemented **one or both of [the options](#wrong-message)**, let's try the new message! Assuming you have 0 xp, it will look like this:
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
If you don't [enable the Confirmation GUI](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml#L49-L51) the below section is not applicable.
## Confirmation GUI
Hmm, we hover over the emerald block and it says "Confirm. Rankup to member", but it doesn't say anything about needing the xp levels. Let's do something about that!
Just like with `requirements-not-met: <text>`, we can use [Option 1](#Option-1)or [Option 2](#Option-2) to remedy the confirmation `gui:`. For this example we'll start with [Option 2](#Option-2).  
Go back to your `locale/` file and find the `gui:` section under `rankup:`.  
![Confirm. Rankup to member.](https://i.imgur.com/US7layr.png)  
### The `gui:` settings used in the image above:
```yaml
  gui:
    rankup:
      material: EMERALD_BLOCK
      # index can be separated by spaces to show in multiple groups
      # for example: 0-3 9-12 18-21
      # you can also just use a single number instead of a range.
      index: 0-3
      name: '&a&lConfirm'
      # lore is optional
      lore: '&6Rankup to &b{RANK}'
    cancel:
      material: REDSTONE_BLOCK
      index: 6-8
      name: '§c§lCancel'
    fill:
      # since all slots are used by , no fill is visible
      name: ' '
      material: BLACK_STAINED_GLASS_PANE
```
The `index` starts at 0 and goes to 8, as you can see in the image below.  
![index for ease of access](https://i.imgur.com/ObvOjki.png)  
To change the lore on the items in the UI to tell players how many xp levels they need for this rankup specifically, we'll use [Option 1](#Option-1). We could use [Option 2](#Option-2) to edit the UI for all rankup steps in the `locale`, but subsequent ranks may not utilize the same requirements which would display incorrect text in the lore like `Costs {AMOUNT xp-level} xp levels.`, similar to `You need {MONEY} money to rankup.`.  
#### Modify your rankups.yml like so:  
```yaml
beginner:
  rank: 'default'
  next: 'member'
  requirements:
  - xp-level 5
  rankup:
    requirements-not-met: "&cYou have {AMOUNT_DONE xp-level}, and need {AMOUNT xp-level} xp levels to rankup!"
    gui:
      rankup:
        material: EMERALD_BLOCK
        index: 0-3
        name: '&a&lConfirm'
        lore: |-
          &6Rankup to &b{RANK}
          &eCosts {AMOUNT xp-level} xp levels.
      #since we don't need to change the cancel or fill sections, we don't need them in the rankup.yml
      #cancel:
        #material: REDSTONE_BLOCK
        #index: 6-8
        #name: '§c§lCancel'  # section sign color codes are also outdated
      #fill:
        #name: ' '
        #material: BLACK_STAINED_GLASS_PANE
```  
#### **NOTE:** the way `lore` is written has changed! Since we wanted 2 lines instead of one, we used **[multiline formatting](https://github.com/okx-code/Rankup3/wiki/FAQ#how-do-i-write-multi-line-messages)** and properly _indented_.  
Save and reload the plugin, then try `/rankup` again.  
![Now showing how much it costs](https://i.imgur.com/Fao0ueo.png)  
This is much better!  
That covers the basics of creating Rankup steps. For more information, look at the comments in the configuration files, check out the **[Advanced Example](https://github.com/okx-code/Rankup3/wiki/Advanced-Configuration-Example)** or look at other pages here on the wiki! (see top-right page-sidebar)
