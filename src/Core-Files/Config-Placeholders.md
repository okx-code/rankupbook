Where config placeholders can be used, all PlaceholderAPI placeholders can be used too.

Old Placeholder | Placeholder | Derived From | Description
 -------------- | ----------- | ------------ | -----------
 `{PLAYER}` | `{{ player }}`  | N/A | The player name.
`{OLD_RANK}` | `{{ rank.rank }}` | [`rank`](https://github.com/okx-code/Rankup3/wiki/How-to-rankups.yml-and-prestiges.yml#2-rank) | The rank the player is currently on.
`{RANK}` | `{{ rank.next }}` | [`next`](https://github.com/okx-code/Rankup3/wiki/How-to-rankups.yml-and-prestiges.yml#3-next) | The rank the player is ranking up to.
`{FROM}` | `{{ from }}` | [`from`](https://github.com/okx-code/Rankup3/wiki/How-to-rankups.yml-and-prestiges.yml#on-from-and-to) | The player's current prestige level.
`{TO}` | `{{ to }}` | [`to`](https://github.com/okx-code/Rankup3/wiki/How-to-rankups.yml-and-prestiges.yml#on-from-and-to) | The player's next prestige level.
`{OLD_RANK_NAME}` | `{{ name.rank }}` | [`display-name`](https://github.com/okx-code/Rankup3/wiki/How-to-rankups.yml-and-prestiges.yml#2-display-name) | The `display-name` for the current rank.
`{RANK_NAME}`| `{{ name.next }}` | [`display-name`](https://github.com/okx-code/Rankup3/wiki/How-to-rankups.yml-and-prestiges.yml#2-display-name) | The `display-name` for the next rank.
`{MONEY}` | `{{ rank.requirement('money').total | money }}` | [`- money <amount>`](https://github.com/okx-code/Rankup3/wiki/List-of-Requirements#list)<br>OR<br>[`- moneyh <amount>`](https://github.com/okx-code/Rankup3/wiki/List-of-Requirements#list)<br>by first in order | The money requirement of the rankup or prestige.
`{MONEY_NEEDED}` | `{{ rank.requirement('money').remaining | money }}` | ([`- money <amount>`](https://github.com/okx-code/Rankup3/wiki/List-of-Requirements#list)<br>OR<br>[`- moneyh <amount>`](https://github.com/okx-code/Rankup3/wiki/List-of-Requirements#list)<br>by first in order)<br>- Vault Balance<br>until <= 0 | The amount more money a player needs to rankup or prestige.
`{AMOUNT <requirement>}` | `{{ rank.requirement('<requirement>').total }}` | [N/A](https://github.com/okx-code/Rankup3/wiki/List-of-Requirements#how-to-specify-sub-requirements-in-placeholders) | The total amount of a requirement a player needs to rankup or prestige.
`{AMOUNT_DONE <requirement>}` | `{{ rank.requirement('<requirement>').progress }}` | [N/A](https://github.com/okx-code/Rankup3/wiki/List-of-Requirements#how-to-specify-sub-requirements-in-placeholders) | The amount of a requirement a player has fulfilled.
`{AMOUNT_NEEDED <requirement>}` | `{{ rank.requirement('<requirement>').remaining }}` | [N/A](https://github.com/okx-code/Rankup3/wiki/List-of-Requirements#how-to-specify-sub-requirements-in-placeholders) | The amount of the requirement a player has left.
`{PERCENT_DONE <requirement>}` | `{{ rank.requirement('<requirement>').percent | percent }}` | [N/A](https://github.com/okx-code/Rankup3/wiki/List-of-Requirements#how-to-specify-sub-requirements-in-placeholders) |
`{PERCENT_LEFT <requirement>}` | `{{ (1 - rank.requirement(req).percent) | percent }}` | [N/A](https://github.com/okx-code/Rankup3/wiki/List-of-Requirements#how-to-specify-sub-requirements-in-placeholders) |
`{SECONDS_LEFT}` | `{{ seconds.remaining }}` | [N/A](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml#L53-L55) | The amount of seconds left on a rankup/prestige cooldown.
`{SECONDS}` | `{{ seconds }} | [N/A](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml#L53-L55) | The total length of the cooldown, in seconds.
