# Confirmation GUI
Hmm, we hover over the emerald block and it says "Confirm. Rankup to member", but it doesn't say anything about needing the xp levels. Let's do something about that!
Just like with `requirements-not-met: <text>`, we can use [Option 1](../Basic-Configuration-Example/Wrong-message.md#option-1)or [Option 2](../Basic-Configuration-Example/Wrong-message.md#option-2) to remedy the confirmation `gui:`. For this example we'll start with [Option 2](../Basic-Configuration-Example/Wrong-message.md#option-2).  
Go back to your `locale/` file and find the `gui:` section under `rankup:`.  
![Confirm. Rankup to member.](https://i.imgur.com/US7layr.png)  
### The gui: settings used in the image above:
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
      lore: '&6Rankup to &b{{ next.rank }}'
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
To change the lore on the items in the UI to tell players how many xp levels they need for this rankup specifically, we'll use [Option 1](../Basic-Configuration-Example/Wrong-message.md#option-1). We could use [Option 2](../Basic-Configuration-Example/Wrong-message.md#option-2) to edit the UI for all rankup steps in the `locale`, but subsequent ranks may not utilize the same requirements which would display incorrect text in the lore like `Costs {rank.requirement('xp-level').total | simple }} xp levels.`, similar to `You need {{ rank.requirement('money').total | money }} money to rankup.`.  
#### Modify your rankups.yml like so:  
```yaml
beginner:
  rank: 'default'
  next: 'member'
  requirements:
  - xp-level 5
  rankup:
    requirements-not-met: "&cYou have {{ rank.requirement('xp-level').progress }}, and need {{ rank.requirement('xp-level').total }} xp levels to rankup!"
    gui:
      rankup:
        material: EMERALD_BLOCK
        index: 0-3
        name: '&a&lConfirm'
        lore: |-
          &6Rankup to &b{{ next.rank }}
          &eCosts {{ rank.requirement('xp-level').total | simple}} xp levels.
      #since we don't need to change the cancel or fill sections, we don't need them in the rankups.yml
      #cancel:
        #material: REDSTONE_BLOCK
        #index: 5-8
        #name: '§c§lCancel'  # section sign color codes are also outdated
      #fill:
        #name: ' '
        #material: BLACK_STAINED_GLASS_PANE
```  
> #### **NOTE:** the way `lore` is written has changed! Since we wanted 2 lines instead of one, we used **[multiline formatting](../Core-Files/FAQ.md#how-do-i-write-multi-line-messages)** and properly _indented_.  

> #### **NOTE:** the _filter_ `simple` applied to the placeholder makes it so the placeholder outputs whole, unformatted numbers. otherwise it would output `5.0`.
Save and reload the plugin, then try `/rankup` again.

![Now showing how much it costs](https://i.imgur.com/Fao0ueo.png)  
This is much better!  
That covers the basics of creating Rankup steps. For more information, look at the comments in the configuration files, check out the **[Advanced Example](../Advanced-Configuration-Example/Back-to-basics.md)** or look at other pages here on the wiki!
