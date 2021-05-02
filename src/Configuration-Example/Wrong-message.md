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