# RanksGUI Settings
Default values can be found on the `master` branch in the github repository [here](../GitHub/Rankup3/locale/en/RanksGUI.html).

```yaml
ranksgui:
  title: "Ranks"
  rows: 3
  offset: 10
  width: 7
```
#### Title
`title:` is the text at the top of the inventory GUI. You can apply color codes to it.
#### Rows
`rows:` defines the number of rows in the inventory GUI. `rows:`  is lower and upper bounded by 1 and 6. Any number in this range is allowed. The Minecraft Inventory doesn't allow for GUIs bigger than 6.
#### Offset
`offset:` defines the slot where the ranks will begin in the inventory. 0 would start the ranks in the very first slot of the inventory (from top left to bottom right). Rankup's default is 10, which is on the second row. This value can be anywhere inside the range of 0 to `rows:` times `width:` minus one. Example: `rows: 6` `width: 9` -> (`6` * `9`) - 1 = 53. Any number outside of your configuration's valid range will cause a range error.
#### Width
`width:` defines the number of tiles occupied by ranks in each row. The default is 7 and the number can range from 1 to 9 inclusive.
###### Visualization of the maximum number of tiles using `offset:`, `rows:`, and `width:`.
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
# there is a Copy to clipboard button at the far edge of this box ->
  rankup: # Make sure you do not have a duplicate `rankup`.
    ranksgui:
      title: "Ranks"
      rows: 3
      offset: 10
      width: 7
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
