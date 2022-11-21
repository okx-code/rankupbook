<meta name="description" content="Tutorial on implementing the RanksGUI screen!">
<meta name="keywords" content="Rankup, Minecraft, Plugin, Spigot, Prestige">
# RanksGUI Settings
Default values can be found on the `master` branch in the github repository [here](../GitHub/Rankup3/locale/en/RanksGUI.html).

```yaml
ranksgui:
  title: "Ranks"
  rows: 3
  width: 7
  offset: 10
```
#### Title
`title:` is the text at the top of the inventory GUI. You can apply color codes to it.
#### Rows
`rows:` defines the number of rows in the inventory GUI. `rows:`  is lower and upper bounded by 1 and 6. Any number in this range is allowed. The Minecraft Inventory doesn't allow for GUIs bigger than 6.
#### Width
`width:` defines the number of tiles occupied by ranks in each row. The default is 7 and the number can range from 1 to 9 inclusive.
#### Offset
`offset:` defines the slot where the ranks will begin in the inventory. 0 would start the ranks in the very first slot of the inventory (from top left to bottom right). Rankup's default is 10, which is on the second row.
## GUI Sizing
Your configuration will provide for a limited range of valid tiles in the inventory to represent rankup steps on the ladder.  
The maximum number of rankup steps which can be displayed is limited to a double chest's inventory (54).  
Using more than 54 rankup steps or misconfiguring the GUI will [cause a range error](../FAQ.md#code-classhljsserver-info-caused-by-javalangarrayindexoutofboundsexception-index-number-out-of-bounds-for-length-number).  
Tiles in the inventory not occupied by a rankup step will use `fill:`.  
The `offset:` value depends on `rows:` and `width:`. Its valid range is always 0 to (`rows:` times `width:`) minus one.  
Example: When `rows: 6` and `width: 9` then (`6` * `9`) - 1 = 53.  
###### Visualization of the maximum number of tiles using `offset: 0`, `rows: 6`, and `width: 9`.
![](https://i.imgur.com/rlLlcrp.png)
## How To Add Lore
#### In `rankups.yml`
Usually the preferred method. Provides settings per-rankup to override the locale.
#### In a [`locale`](../GitHub/Rankup3/locale.html)
Allows changing all rankup step GUIs from a single file like [`en.yml`](../GitHub/Rankup3/locale/en.html). This is especially useful for configurations where requirements for each rankup step are all the same/similar or when managing a ladder with lots of rankup steps.
### Instructions
In your `rankups.yml` **or** locale file add `lore:` under `complete:`, `current:`, and `incomplete:` inside [`ranksgui:`](../GitHub/Rankup3/locale/en/RanksGUI.html). Add the `ranksgui:` section if it isn't present.

Alternatively, for _**each**_ rankup step in `rankups.yml` paste a copy the following:
```yaml
  rankup: # Make sure you do not have a duplicate `rankup`.
    ranksgui:
      title: "Ranks"
      rows: 3
      width: 7
      offset: 10
      complete:
        material: GREEN_STAINED_GLASS_PANE
        name: "&aRank &7{{ next.rank }} &a(completed)"
        lore: "Very Lore"
      current:
        material: ORANGE_STAINED_GLASS_PANE
        name: "&dRankup to &7{{ next.rank }}"
        lore: "Much\nLore"
      incomplete:
        material: RED_STAINED_GLASS_PANE
        name: "&cRank &7{{ next.rank }} &c(requires rankup)"
        lore: |-
          Wow
          Lore
      # fill: can use all of material: name: lore: too!
```
We recommend the [FAQ on _YAML questions_](../FAQ.md#how-do-i-write-multi-line-messages) for more information on _multi-line_ syntax used in this `lore:` example.

## Customize Your Items!
- Make `material:` for `incomplete:`, `current:`, and `complete:` to customize the items your rankups use at each state and even per step! Item names must match the name in the [**Spigot ENUM**](../Spigot/Docs/materials.html) for materials.
