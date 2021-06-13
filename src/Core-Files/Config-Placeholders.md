## Sub-requirements in placeholders

Requirements that support sub-requirements are used in the format `<requirement> <sub-requirement> <amount>`. In placeholders, sub-requirements are `<requirement>#<sub-requirement>`.

For example, with **[Config Placeholders](../Core-Files/Config-Placeholders.md)** you have:

`{{ rank.requirement('block-break#STONE').total | simple }}`

Or in [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/): 

`%rankup_requirement_block-break#STONE%`
#### Read [this page](../Core-Files/PAPI-Placeholders.md) for more information about Rankup PAPI placeholders.

Use the spigot enum pages for [entities](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/package-summary.html) and [items](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/material/package-summary.html) when declared in requirements.

## PAPI placeholders inside Rankup's internal placeholders

It's possible to put a PAPI placeholder inside an internal placeholder. It goes in the spot where the inbuilt requirement would go normally.

Example:
```yaml
header:
  rank: 'currentRank'
  next: 'nextRank'
  requirements:
    - 'placeholder %statistic_hours_played% >= 12'
  rankup:
    requirements-not-met: |-
      You need:
      {{ rank.requirement('placeholder#%statistic_hours_played%').total | simple }} hours of playtime.
      to rank up to {{ next.rank }}!
```

## Config Placeholders

Where config placeholders can be used, all PlaceholderAPI placeholders can be used too.

> ### **NOTE:** Some placeholders output an unecessary decimal.
> example requirement `xp-level 5` with placeholder `{{rank.requirement('xp-level').total}}` will output `5.0`.
> To combat this, use the `simple` _filter_ like so:
> `{{rank.requirement('xp-level').total | simple}}`

Old Placeholder | Placeholder | Derived From | Description
--------------- | ----------- | ----------- | -----------
`{PLAYER}`  | `{{ player }}` | N/A | The player name.
`{OLD_RANK}` | `{{ rank.rank }}` | [`rank`](../Rankups-and-prestiges/How-to-rankups.yml.md#2-rank) | The rank the player is currently on.
`{RANK}` | `{{ next.rank }}` | [`next`](../Rankups-and-prestiges/How-to-rankups.yml.md#3-next) | The rank the player is ranking up to.
`{FROM}` | `{{ rank.from }}` | [`from`](../Rankups-and-prestiges/How-to-prestiges.yml.md#on-from-and-to) | The player's current prestige level.
`{TO}` | `{{ rank.to }}` | [`to`](../Rankups-and-prestiges/How-to-prestiges.yml.md#on-from-and-to) | The player's next prestige level.
`{OLD_RANK_NAME}` | `{{ name.rank }}` | [`display-name`](../Rankups-and-prestiges/Optionals.md#2-display-name) | The `display-name` for the current rank.
`{RANK_NAME}` | `{{ name.next }}` | [`display-name`](../Rankups-and-prestiges/Optionals.md#2-display-name) | The `display-name` for the next rank.
`{MONEY}` | `{{ rank.requirement('money').total \| money }}` | [`- money <amount>`](../Core-Files/List-of-Requirements.md#list)<br>OR<br>[`- moneyh <amount>`](../Core-Files/List-of-Requirements.md#list)<br>by first in order | The money requirement of the rankup or prestige.
`{MONEY_NEEDED}` | `{{rank.requirement('money').remaining \| money }}` | ([`- money <amount>`](../Core-Files/List-of-Requirements.md#list)<br>OR<br>[`- moneyh <amount>`](../Core-Files/List-of-Requirements.md#list)<br>by first in order)<br>- Vault Balance<br>until <= 0 | The amount more money a player needs to rankup or prestige.
`{AMOUNT <requirement>}` | `{{ rank.requirement('<requirement>').total }}` | [N/A](../Core-Files/List-of-Requirements.md#list) | The total amount of a requirement a player needs to rankup or prestige.
`{AMOUNT_DONE <requirement>}` | `{{ rank.requirement('<requirement>').progress }}` | [N/A](../Core-Files/List-of-Requirements.md#list) | The amount of a requirement a player has fulfilled.
`{AMOUNT_NEEDED <requirement>}` | `{{ rank.requirement('<requirement>').remaining }}` | [N/A](../Core-Files/List-of-Requirements.md#list) | The amount of the requirement a player has left.
`{PERCENT_DONE <requirement>}` | `{{ rank.requirement('<requirement>').percent \| percent }}` | [N/A](../Core-Files/List-of-Requirements.md#list) |
`{PERCENT_LEFT <requirement>}` | `{{ (1 - rank.requirement('<requirement>').percent) \| percent }}` | [N/A](../Core-Files/List-of-Requirements.md#list) | |
`{SECONDS_LEFT}` | `{{ seconds.remaining }}` | [N/A](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml#L53-L55) | The amount of seconds left on a rankup/prestige cooldown.
`{SECONDS}` | `{{ seconds }}` | [N/A](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml#L53-L55) | The total length of the cooldown, in seconds.