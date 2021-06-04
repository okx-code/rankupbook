# Placeholder Engine

### Text templating uses [Pebble](https://pebbletemplates.io/). All functions and variables found on there will work in Rankup as well.
> #### The following examples use spaces between the placeholder and the curly brackets. The spaces are not necessary, but we included them for easier readability. Feel free to remove them in your config.

## Context Reference

Most of the following values are available as the context, if it makes sense for the message.
Placeholder | Alias | Description
----------- | ----- | -----------
`{{ player }}` | N/A | Username of the player.
`{{ rank.rank }}` | `{{ rank }}` | The current rank of the player.
`{{ next.rank }}` | `{{ next }}` | The next rank of the player.
`{{ rank.name }}` | N/A | The `display-name` for the current rank the player is on.
`{{ next.name }}` | N/A | The `display-name` for the next rank the player is on.
`{{ rank.from }}` | `{{ from }}` | The current prestige of the player.
`{{ rank.to }}` | `{{ to }}` | The next prestige of the player.
`{{ ranks }}` | N/A | A list of all ranks seperated by commas.
`{{ ranks[<index>] }}` | N/A | Similar to `{{ ranks }}` but for a specific rank. `<index>` must be a number.
`{{ rank.requirement('<requirement>') }}` | N/A | Get a specific requirement for the rank the player is on.
`{{ requirements[] }}` | N/A | A full list of requirements for the rank the player is on.
`{{ seconds }}` | N/A | Total cooldown in seconds before you can rankup again.
`{{ seconds_left }}` | N/A | What's left of the cooldown in seconds before you can rankup again.

## Requirement Methods

Methods tell the placeholder engine what part of the result you want.

Suffix | Description | Example
--- | --- | --- 
`done` | True or false depending on if the requirement is complete. | `{{ rank.requirement('money').done }}`
`total` | Displays total amount required. | `{{ rank.requirement('money').total }}`
`progress` | Amount done of a requirement. | `{{ rank.requirement('money').progress }}`
`remaining` | Amount left of a requirement. | `{{ rank.requirement('money').remaining }}`
`percent` | Goes from 0 to 1. For actual percentage apply as tunnel. | `{{ rank.requirement('money').percent }}`
`name` | Get the `display-name` of the specified rank. | `{{ rank[2].name }}`

## Filters

Filters serve to format the original result to fit your purpose better. The following filters were custom-made for Rankup.
> Find the built-in filters [here](https://pebbletemplates.io/wiki/filter/abbreviate/).

Filter | Description | Example
------ | ----------- | -------
`percent` | Formats result to be ##.#. Use with `percent` suffix. | `{{ rank.requirement('money').percent | percent }}`
`money` | Formats result to be ###,###.##. | `{{ rank.requirement('money').total | money }}`
`simple` | Formats result to be whole numbers. | `{{ rank.requirement('xp-level').total | simple }}`
