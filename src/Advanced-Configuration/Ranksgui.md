# RanksGUI Settings
RanksGUI has some setting you can tweak to get the desired look for your ranksGUI. This is the explanation of what they do.

###### The settings in question.
```yaml
ranksgui:
  title: "Ranks"
  rows: 3
  offset: 10
  width: 7
```
### Title
Title is the text that you can see above in the GUI. You can apply color codes to it.

### Rows
Rows are the amount of horizontal lines in the GUI. Rankup by default has 3, but the maximum is 6. The minimum is 1. Unfortunately Minecraft doesn't allow for bigger GUIs.

### Offset
Offset defines the slot where the ranks will begin. By default it's 10, but it can be anywhere inside the range of 0 to 53. Anything outside of that range will cause errors.

### Width
Width is how many ranks are on each `row`. The default is 7, but the range can be between 1 and 9. Since a row has an odd amount of slots, we recommend you also pick an odd number to maintain symmetry.

###### Visualization of the `offset` range and amount of `rows`.
![](https://i.imgur.com/rlLlcrp.png)

# How To Add Lore
- In [`rankups.yml`](../Advanced-Configuration/Ranksgui.md#Rankupsyml)
- In the [`locale`](../Advanced-Configuration/Ranksgui.md#Rankupsyml)

### In the `Rankups.yml`.
Usually the preferred method.

### Usecases
- Individual lore for each rankup step.
- Increased control over lore
- Per-rankup ranksgui settings.

### Instructions
- In your `rankups.yml`

For _**each**_ rankup step do the following:
- Make sure you do not have a duplicate `rankup`.
- Copy the below configuration.
  - Read the _comments_ carefully!

We recommend you check out [our FAQ on _YAML questions_](../FAQ.md#how-do-i-write-multi-line-messages) for more information about _multi-line_ syntax.

```yaml
Header:
  rank: 'currentRank'
  next: 'nextRank'
  requirements:
    - 'yourRequirementsHere'
# The following notes will not impact anything and can safely be removed.
  rankup: # IMPORTANT: Copy from here if you DO NOT have this section already.
    ranksgui: # Copy from here if you already have a "rankup" section.
      title: "Ranks"
      rows: 3
      offset: 10
      width: 7
      complete:
        material: GREEN_STAINED_GLASS_PANE
        name: "&aRank &7{{ next.rank }} &a(completed)"
        lore:
      current:
        material: ORANGE_STAINED_GLASS_PANE
        name: "&dRankup to &7{{ next.rank }}"
        lore:
      incomplete:
        material: RED_STAINED_GLASS_PANE
        name: "&cRank &7{{ next.rank }} &c(requires rankup)"
        lore:
```
### 2. In the locale

### Usecases
- Global changed for the GUI
- Same requirements for each rankup step.

### Instructions
- In your [`locale`](https://github.com/okx-code/Rankup3/tree/master/src/main/resources/locale). ([`en.yml`](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/locale/en.yml) by default)

Scroll down to [`line 38`](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/locale/en.yml#L38-L54).
- Under the `complete`, `current` and `incomplete` sections.
- Under `name`. (On the same level of _indentation_)
- Add the text `lore:`

It should look like this:
```yml
  ranksgui: # You can completely replace the "ranksgui" section you currently have.
    title: "Ranks"
    rows: 3
    offset: 10
    width: 7
    complete:
      material: GREEN_STAINED_GLASS_PANE
      name: "&aRank &7{{ next.rank }} &a(completed)"
      lore:
    current:
      material: ORANGE_STAINED_GLASS_PANE
      name: "&dRankup to &7{{ next.rank }}"
      lore:
    incomplete:
      material: RED_STAINED_GLASS_PANE
      name: "&cRank &7{{ next.rank }} &c(requires rankup)"
      lore:
    fill:
      material: BLACK_STAINED_GLASS_PANE
      name: ' '
```

### Customize your Ranksgui!
- Make `material` for `incomplete`, `current` and `complete` the same material but different for each rankup step so when you open the GUI each rank has its own item. materials must match the **[Spigot ENUM](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html)**
