# Config Placeholders

Where config placeholders can be used, all PlaceholderAPI placeholders can be used too.

These placeholders will only work inside the context of Rankup! This means that if you use the in a message from another plugin, they won't register!

| Placeholder | Derived From | Description
| ----------- | ----------- | -----------
| `{PLAYER}`  | N/A | The player name.
| `{OLD_RANK}` | [`rank`](https://github.com/okx-code/Rankup3/wiki/How-to-rankups.yml-and-prestiges.yml#2-rank) | The rank the player is currently on.
| `{RANK}` | [`next`](https://github.com/okx-code/Rankup3/wiki/How-to-rankups.yml-and-prestiges.yml#3-next) | The rank the player is ranking up to.
| `{FROM}` | [`from`](https://github.com/okx-code/Rankup3/wiki/How-to-rankups.yml-and-prestiges.yml#on-from-and-to) | The player's current prestige level.
| `{TO}` | [`to`](https://github.com/okx-code/Rankup3/wiki/How-to-rankups.yml-and-prestiges.yml#on-from-and-to) | The player's next prestige level.
| `{OLD_RANK_NAME}` | [`display-name`](https://github.com/okx-code/Rankup3/wiki/How-to-rankups.yml-and-prestiges.yml#2-display-name) | The `display-name` for the current rank.
| `{RANK_NAME}` | [`display-name`](https://github.com/okx-code/Rankup3/wiki/How-to-rankups.yml-and-prestiges.yml#2-display-name) | The `display-name` for the next rank.
| `{MONEY}` | [`- money <amount>`](https://github.com/okx-code/Rankup3/wiki/List-of-Requirements#list)<br>OR<br>[`- moneyh <amount>`](https://github.com/okx-code/Rankup3/wiki/List-of-Requirements#list)<br>by first in order | The money requirement of the rankup or prestige.
| `{MONEY_NEEDED}` | ([`- money <amount>`](https://github.com/okx-code/Rankup3/wiki/List-of-Requirements#list)<br>OR<br>[`- moneyh <amount>`](https://github.com/okx-code/Rankup3/wiki/List-of-Requirements#list)<br>by first in order)<br>- Vault Balance<br>until <= 0 | The amount more money a player needs to rankup or prestige.
| `{AMOUNT <requirement>}` | [N/A](https://github.com/okx-code/Rankup3/wiki/List-of-Requirements#how-to-specify-sub-requirements-in-placeholders) | The total amount of a requirement a player needs to rankup or prestige.
| `{AMOUNT_DONE <requirement>}` | [N/A](https://github.com/okx-code/Rankup3/wiki/List-of-Requirements#how-to-specify-sub-requirements-in-placeholders) | The amount of a requirement a player has fulfilled.
| `{AMOUNT_NEEDED <requirement>}` | [N/A](https://github.com/okx-code/Rankup3/wiki/List-of-Requirements#how-to-specify-sub-requirements-in-placeholders) | The amount of the requirement a player has left.
| `{PERCENT_DONE <requirement>}` | [N/A](https://github.com/okx-code/Rankup3/wiki/List-of-Requirements#how-to-specify-sub-requirements-in-placeholders) |
| `{PERCENT_LEFT <requirement>}` | [N/A](https://github.com/okx-code/Rankup3/wiki/List-of-Requirements#how-to-specify-sub-requirements-in-placeholders) |
| `{SECONDS_LEFT}` | [N/A](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml#L53-L55) | The amount of seconds left on a rankup/prestige cooldown.
| `{SECONDS}` | [N/A](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml#L53-L55) | The total length of the cooldown, in seconds.
