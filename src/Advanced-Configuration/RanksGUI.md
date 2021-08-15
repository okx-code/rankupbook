# RanksGUI Settings
Default values can be found in the `master` branch in the github repository <a href="https://github.com/okx-code/Rankup3/blob/master/src/main/resources/locale/en.yml#L38-L54" target="_blank">here</a>.

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
###### Visualization of the maximum `offset:`, `rows:`, and `width:`.
![Visualization of the maximum `offset:`, `rows:`, and `width:`.](https://i.imgur.com/rlLlcrp.png)
## How To Add Lore
#### In `rankups.yml`
Usually the preferred method.
#### Usecases
- Individual lore for each rankup step.
- Increased control over lore
- Per-rankup ranksgui settings.
#### In a <a href="https://github.com/okx-code/Rankup3/tree/master/src/main/resources/locale" target="_blank">`locale`</a>

#### Usecases
- Changing all rankup step GUIs from a single file like <a href="https://github.com/okx-code/Rankup3/blob/master/src/main/resources/locale/en.yml" target="_blank">`en.yml`</a>
- Same/Similar requirements for each rankup step
- Managing a ladder with lots of rankup steps
### Instructions
In your `rankups.yml` **or** locale file add `lore:` under the `complete`, `current`, and `incomplete` sections inside [`ranksgui:`](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/locale/en.yml#L38-L54) section. Add the entire `ranksgui:` section if it isn't present.

Alternatively, for _**each**_ rankup step copy the following:
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
      # fill: can use lore: too!
```
We recommend you check out [our FAQ on _YAML questions_](../FAQ.md#how-do-i-write-multi-line-messages) for more information about _multi-line_ syntax.

## Customize Your Items!
- Make `material:` for `incomplete`, `current`, and `complete` to customize the items your rankups use at each state and even per step! Item names must match the name in the **[Spigot ENUM](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html)** for materials.
