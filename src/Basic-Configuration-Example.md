# Minimum Requirements to use Rankup:
* Vault
* Vault-Compatible Group Management Plugin
* Pre-defined Permission Groups in prior Plugin for each rank/prestige.
## Verify `config.yml` contains [`permission-rankup: false`](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml#L41-L47) (default)
## This example does not cover [`permission-rankup: true`](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml#L41-L47)
# Steps and Ladders
### Each Rankup or Prestige is a step on their respective ladder.
### Each Prestige can also slide players down or up the Rankup ladder.
### `/ranks` displays the entire Rankup "Ladder" or discrete set of available Rankup steps.
### `/prestiges` displays the entire Prestige "Ladder" [when enabled](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml#L21).
***
# Your First Rank
The first time you start your server **with Rankup installed** the default **[rankups.yml](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/rankups.yml)**, **[config.yml](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml)**, and **[locale](https://github.com/okx-code/Rankup3/tree/master/src/main/resources/locale)** will generate like **[this](https://github.com/okx-code/Rankup3/tree/master/src/main/resources)**. Stop your server once the plugins have loaded. The **[rankups.yml](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/rankups.yml)** file is where you will add your ranks to. We recommend you take your time to read through it and all the comments.
#### [See this FAQ section before continuing the tutorial!](https://github.com/okx-code/Rankup3/wiki/FAQ#YAML-Questions)
## Starting to Format
* [Each rankup needs a `heading:`, `rank:`, `next:`, and `requirements:` to be valid.](https://github.com/okx-code/Rankup3/wiki/How-to-rankups.yml-and-prestiges.yml#these-are-the-4-required-sections-in-the-rankupsyml-file-necessary-for-a-rankup-to-be-considered-valid-individually)
* You can only have one starter rank as multiple _"roots"_ aren't possible. Multiple roots will cause the following error:
`[Server] ERROR [Rankup] Multiple root rankup nodes detected (a root rankup nodes is a rankup that does not have anything that ranks up to it). This may lead to inconsistent behaviour.`
* The last rankup of a ladder (all the ranks) should refer to the last rank in `next:`. This rank should not be the `rank:` of any other step.
* The prior also applies to prestiges' `rank:` and `next:`.  
**IMPORTANT:** If you change the configuration file while the server is running, some settings may not be applied until the next restart. However, you can safely work on the rankups.yml, prestiges.yml, and locale files while the server is running and use the command `/rankup3 reload` or `/pru reload` to apply saved changes from those files. **Reloading Rankup with the command will not cause issues**. Errors may occur while reloading when the files contain [invalid user-generated YAML code](https://github.com/okx-code/Rankup3/wiki/FAQ#YAML-Questions).  

**[LuckPerms](https://www.spigotmc.org/resources/luckperms-an-advanced-permissions-plugin.28140/)** is strongly recommended and will be used throughout the below examples to manage our groups.

### First Example
This example will provide the basis for the entire tutorial.
```yaml
defaultToMember:
  rank: 'default'
  next: 'member'
  requirements:
    - 'xp-level 5' # the indentation of 2 spaces is very important
    # YAML files are whitespace and format sensitive.
```
#### First Example Line By Line Breakdown:
1. [`defaultToMember:`](https://github.com/okx-code/Rankup3/wiki/How-to-rankups.yml-and-prestiges.yml#1-heading) Indicates the subsequent indendented subsections are part of a rankup step on the ladder. The text `defaultToMember` must only be unique from all other `heading:` sections.
2. [`rank: 'default'`](https://github.com/okx-code/Rankup3/wiki/How-to-rankups.yml-and-prestiges.yml#2-rank) Sets the group players must be in to be able to use this rankup step from "default". (`default` is our example current group in {OLD_RANK})
3. [`next: 'member'`](https://github.com/okx-code/Rankup3/wiki/How-to-rankups.yml-and-prestiges.yml#3-next) Sets the group assigned to the player when they've met the requirements and use `/rankup` to complete this rankup to "member". (`'member'` is our example next group in {RANK})
4. [`requirements:`](https://github.com/okx-code/Rankup3/wiki/How-to-rankups.yml-and-prestiges.yml#4-requirements) This begins the list of requirements section.
5. [`- xp-level 5`](https://github.com/okx-code/Rankup3/wiki/List-of-Requirements) This example assumes the only requirement we want for a player to rankup is 5 xp levels as deducted (as a sort of payment). If we wanted to let players keep their xp levels when ranking up, we could check how many xp levels they _have_ with `xp-levelh` (compare) instead of `xp-level` (deduct). Rankup will only take the given number of any requirement (`xp-level 5` here) away once a player successfully ranks up. We only used one requirement for this example, but you can have many different kinds of **[requirements](https://github.com/okx-code/Rankup3/wiki/List-of-Requirements)** by following the above format.  

Follow the links provided in 1 through 5 to see more detailed descriptions of these sections.  

After replacing the default example in rankups.yml with the [first example](#First-Example), now we're ready to `/pru reload` or `/rankup3 reload` to apply the changes while the server is running.
###### The plugin used to be called PrisonRankup, which is why [pru is still an alias](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/plugin.yml#L13-L16).
## Group Management
Assuming all users start with the 'default' group, anyone should be able to immediately see the rankup as `Current` or in-progress!  
Before trying to complete the rankup, let's create the group `member`, otherwise Rankup won't change the player's groups.  
To create our group we'll be using the **[LuckPerms creategroup](https://luckperms.net/wiki/General-Commands#lp-creategroup-name-weight-displayname)** command.
```
/lp creategroup member
```
Now, make sure your primary group in LP is `default` and then type /rankup to rankup the ladder to member.  
Let's say you **don't have** the xp levels needed. It will say in chat:
```
You need {MONEY} money to rankup.
```
You might think something went wrong, but that's not the case! This is the default message when you don't meet some requirements.  
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
