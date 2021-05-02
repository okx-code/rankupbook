## Config PAPI Placeholders
**Note:** Placeholders are included within the Rankup plugin, a downloaded expansion is not required.

| Placeholder | Description
| ----------- | -----------
| `%rankup_current_rank%` | The rank a player is in.
| `%rankup_next_rank%` | The rank a player can rankup to.
| `%rankup_current_prestige%` | The prestige rank a player is in.
| `%rankup_next_prestige%` | The next prestige rank for the player.
| `%rankup_money%` | The money requirement for a player to /rankup.
| `%rankup_money_formatted%` | As above, but formatted. By default, this might look like `1,000.00` instead of `1000.0`
| `%rankup_prestige_money%` |
| `%rankup_prestige_money_formatted%` |
| `%rankup_money_left%` |
| `%rankup_money_left_formatted%` |
| `%rankup_percent_left%` |
| `%rankup_percent_left_formatted%` |
| `%rankup_percent_done_formatted%` |
| `%rankup_percent_done_formatted%` |
| `%rankup_requirement_<requirement>[_<done/left/percent_left/percent_done>]` | The \<requirement> to /rankup. See **[requirements](https://github.com/okx-code/Rankup3/wiki/Requirements)**. `%rankup_requirement_xp-level_left%` is equivalent to `{AMOUNT_NEEDED xp-level}`
| `%rankup_rank_requirement_<rank>_<requirement>[_<left/percent_left/percent_done>]%` | As above, but for ranking up to a certain `<rank>`
| `%rankup_rank_money_<rank>%` | The money requirement to rankup from **<rank>**. This is formatted.
| `%rankup_rank_money_<rank>_left%` |
| `%rankup_status_<rank>%` | The status of the rank of the given rank for the player. By default, returns "Complete" for rankups the player has completed, "Current" for the rankup the player is currently in, and "Incomplete" for rankups the player has not completed.
