<html>
  <head>
    <meta name="description" content="Reference for the provided PAPI Placeholders.">
    <meta name="keywords" content="Rankup, Minecraft, Plugin, Spigot, Prestige">
  </head>
</html>

## MVdW Placeholders
To use these placeholders in FeatherBoard (or any plugin using MVdW placeholders) you must use `{placeholderapi_<placeholder>}` instead of `%placeholder%`. For example, you might use `{placeholderapi_rankup_current_rank}` instead of `%rankup_current_rank%` in FeatherBoard.

> ## Using PAPI as a Requirement
> Learn how to use a PAPI placeholder as a requirement [here](./Advanced-Configuration/Adding-Custom-Requirements.md)!

## Config PAPI Placeholders
> #### Placeholders are included with Rankup. `No download required`.

| Placeholder | Description
| ----------- | -----------
| `%rankup_current_rank%` | Rank the player is currently in.
| `%rankup_current_rank_name%` | The display name of a rank a player is in.
| `%rankup_next_rank%` | Rank the player will rank up to.
| `%rankup_next_rank_name%` | The display name of a rank a player can rankup to.
| `%rankup_current_prestige%` | Prestige the player is currently in.
| `%rankup_current_prestige_name%` | The prestige rank's display name a player is in.
| `%rankup_next_prestige%` | Prestige the player will prestige to.
| `%rankup_next_prestige_name%` | The next prestige rank's display name for the player.
| `%rankup_prestige_money%` | `money` requirement to prestige
| `%rankup_prestige_money_formatted%` | As above, but formatted.<br>`1000` becomes `1K`.
| `%rankup_money%` | Total amount of `money` requirement to rank up.
| `%rankup_money_formatted%` | As above, but formatted.<br>`1000` becomes `1K`.
| `%rankup_money_left%` | Amount left to complete `money` requirement.
| `%rankup_money_left_formatted%` | As above, but formatted.<br>`1000` becomes `1K`.
| `%rankup_percent_done%` | Exact amount done in percent for `money` requirement.
| `%rankup_percent_left%` | Exact amount left in percent for `money` requirement.
| `%rankup_percent_done_formatted%` | Amount done in percent for `money` requirement. Formatted to 2 decimals.
| `%rankup_percent_left_formatted%` | Amount left in percent for `money` requirement. Formatted to 2 decimals.
| `%rankup_requirement_<requirement>%` | Total amount of `<requirement>`. See [**requirements**](./List-of-Requirements.md#List).
| `%rankup_requirement_<requirement>_done%` | Amount done of `<requirement>`.
| `%rankup_requirement_<requirement>_left%` | Amount left of `<requirement>`.
| `%rankup_requirement_<requirement>_percent_done%` | Amount done of `<requirement>` in percent.
| `%rankup_requirement_<requirement>_percent_left%` | Amount left of `<requirement>` in percent.
| `%rankup_rank_requirement_<rank>_<requirement>%` | Total Amount of `<requirement>` for `<rank>`.
| `%rankup_rank_requirement_<rank>_<requirement>_done%` | Amount done of `<requirement>` for `<rank>`.
| `%rankup_rank_requirement_<rank>_<requirement>_left%` | Amount left of `<requirement>` for `<rank>`.
| `%rankup_rank_requirement_<rank>_<requirement>_percent_done>%` | Amount done of `<requirement>` for `<rank>` in percent.
| `%rankup_rank_requirement_<rank>_<requirement>_percent_left%` | Amount left of `<requirement>` for `<rank>` in percent.
| `%rankup_rank_money_<rank>%` | Amount of `money` requirement to rankup from `<rank>`, formatted.
| `%rankup_rank_money_<rank>_left%` | Amount left of `money` requirement to rankup from `<rank>`, formatted.
| `%rankup_status_<rank>%` | The status of the specified `<rank>` for the player. Customize [**here**](./GitHub/Rankup3/config/Status.html).
