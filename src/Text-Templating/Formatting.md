# Formatting

Here you can find all the information you need to know about how and what you can format.

## Requirements

Methods tell the placeholder engine what part of the result you want.

Suffix | Description | Example
--- | --- | --- 
`done` | True or false depending on if the requirement is complete. | `{{ rank.requirement('money').done }}`
`total` | Displays total amount required. | `{{ rank.requirement('money').total }}`
`progress` | Amount done of a requirement. | `{{ rank.requirement('money').progress }}`
`remaining` | Amount left of a requirement. | `{{ rank.requirement('money').remaining }}`
`percent` | Goes from 0 to 100. | `{{ rank.requirement('money').percent }}`
`quotient` | Like percent, but goes from 0 to 1. | `{{ rank.requirement('money').quotient }}`

## Filters

<a href="https://pebbletemplates.io/wiki/filter/abbreviate/" target="_blank">Filters</a> serve to format the original result to fit your purpose better. The following filters were custom-made for Rankup: `simple`, `money` and `percent`. They use the number formatting found in the `placeholders` section of Rankup's `config.yml`. The pipe symbol `|` and the filter name will apply it. Here are some examples:

Filter | Description | Example
------ | ----------- | -------
`percent` | Formats result to be ##.#. Use with `percent` method. | `{{ rank.requirement('money').percent \| percent }}`
`money` | Formats result to be ###,###.##. | `{{ rank.requirement('money').total \| money }}`
`simple` | Formats result to be whole numbers. | `{{ rank.requirement('xp-level').total \| simple }}`

Using filters is recommended for displaying any non-integer number to a player, otherwise the formatting may not be as desired (for example you can get something like 0.2000000001 or 4.0). The `simple` filter is recommended for most use cases.
