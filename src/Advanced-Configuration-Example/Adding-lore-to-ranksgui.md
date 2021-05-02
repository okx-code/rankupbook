# Adding Lore to `ranksgui:`  
### 1. In the `locale`
Go to your **translation file** (`en.yml` by default) and scroll down to `line 41` and under each section (`complete`, `current` and `incomplete`) add under `name` **on the same level of indentation** the text `lore:`

It should look like this:
```yml
  ranksgui:
    title: "Ranks"
    rows: 3
    offset: 10
    width: 7
    complete:
      material: GREEN_STAINED_GLASS_PANE
      name: "&aRank &7{RANK} &a(completed)"
      lore: "Very Lore"
    current:
      material: ORANGE_STAINED_GLASS_PANE
      name: "&dRankup to &7{RANK}"
      lore: "Much\nLore"
    incomplete:
      material: RED_STAINED_GLASS_PANE
      name: "&cRank &7{RANK} &c(requires rankup)"
      lore: |-
        Wow
        Lore
    fill:
      material: BLACK_STAINED_GLASS_PANE
      name: ' '
```
### 2. In the `Rankups.yml`.
This is usually the preferred method but a bit more effort goes into it as well.

Go to your Rankups.yml, and add the following to __**each**__ rank:
```yaml
RankName:
  rank: 'currentRank'
  next: 'nextRank'
  requirements:
    - 'yourRequirementsHere'
  rankup: #start copying from this part! This note won't impact anything and can be removed. 
    ranksgui:
      title: "Ranks"
      rows: 3
      offset: 10
      width: 7
      complete:
        material: GREEN_STAINED_GLASS_PANE
        name: "&aRank &7{RANK} &a(completed)"
        lore: "Very Lore"
      current:
        material: ORANGE_STAINED_GLASS_PANE
        name: "&dRankup to &7{RANK}"
        lore: "Much\nLore"
      incomplete:
        material: RED_STAINED_GLASS_PANE
        name: "&cRank &7{RANK} &c(requires rankup)"
        lore: |-
          Wow
          Lore
      fill:
        material: BLACK_STAINED_GLASS_PANE
        name: ' '
