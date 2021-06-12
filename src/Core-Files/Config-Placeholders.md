# Config Placeholders

Where config placeholders can be used, all PlaceholderAPI placeholders can be used too.  
These placeholders only work inside Rankup's messages! See the [list of Rankup's PAPI expansion](..Core-Files/PAPI-Placeholders.html#config-papi-placeholders) for external use!

| Placeholder | Derived From | Description
| ----------- | ----------- | -----------
| `{PLAYER}`  | N/A | The player name.
| `{OLD_RANK}` | [`rank`](../Rankups-and-prestiges/How-to-rankups.yml.md#2-rank) | The rank the player is currently on.
| `{RANK}` | [`next`](../Rankups-and-prestiges/How-to-rankups.yml.md#3-next) | The rank the player is ranking up to.
| `{FROM}` | [`from`](../Rankups-and-prestiges/How-to-prestiges.yml.md#on-from-and-to) | The player's current prestige level.
| `{TO}` | [`to`](../Rankups-and-prestiges/How-to-prestiges.yml.md#on-from-and-to) | The player's next prestige level.
| `{OLD_RANK_NAME}` | [`display-name`](../Rankups-and-prestiges/Optionals.md#2-display-name) | The `display-name` for the current rank.
| `{RANK_NAME}` | [`display-name`](../Rankups-and-prestiges/Optionals.md#2-display-name) | The `display-name` for the next rank.
| `{MONEY}` | [`- money <amount>`](../Core-Files/List-of-Requirements.md#list)<br>OR<br>[`- moneyh <amount>`](../Core-Files/List-of-Requirements.md#list)<br>by first in order | The money requirement of the rankup or prestige.
| `{MONEY_NEEDED}` | ([`- money <amount>`](../Core-Files/List-of-Requirements.md#list)<br>OR<br>[`- moneyh <amount>`](../Core-Files/List-of-Requirements.md#list)<br>by first in order)<br>- Vault Balance<br>until <= 0 | The amount more money a player needs to rankup or prestige.
| `{AMOUNT <requirement>}` | [N/A](../Core-Files/List-of-Requirements.md#list) | The total amount of a requirement a player needs to rankup or prestige.
| `{AMOUNT_DONE <requirement>}` | [N/A](../Core-Files/List-of-Requirements.md#list) | The amount of a requirement a player has fulfilled.
| `{AMOUNT_NEEDED <requirement>}` | [N/A](../Core-Files/List-of-Requirements.md#list) | The amount of the requirement a player has left.
| `{PERCENT_DONE <requirement>}` | [N/A](../Core-Files/List-of-Requirements.md#list) |
| `{PERCENT_LEFT <requirement>}` | [N/A](../Core-Files/List-of-Requirements.md#list) |
| `{SECONDS_LEFT}` | [N/A](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml#L53-L55) | The amount of seconds left on a rankup/prestige cooldown.
| `{SECONDS}` | [N/A](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml#L53-L55) | The total length of the cooldown, in seconds.
