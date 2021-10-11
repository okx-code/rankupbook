<html>
  <head>
    <meta name="description" content="Reference for rankup's provided Pebble Formatting suffixes and filters.">
    <meta name="keywords" content="Rankup, Minecraft, Plugin, Spigot, Prestige">
  </head>
</html>

## Requirements

Methods tell the placeholder engine what part of the result you want.

Suffix | Description | Example
- | - | -
`done` | True or false depending on if the requirement is complete. | `{{ rank.requirement('money').done }}`
`total` | Displays total amount required. | `{{ rank.requirement('money').total }}`
`progress` | Amount done of a requirement. | `{{ rank.requirement('money').progress }}`
`remaining` | Amount left of a requirement. | `{{ rank.requirement('money').remaining }}`
`percent` | Goes from 0 to 100. | `{{ rank.requirement('money').percent }}`
`quotient` | Like percent, but goes from 0 to 1. | `{{ rank.requirement('money').quotient }}`

## Filters

> The pipe symbol `|` and the filter name will apply it.  
> [Filters](../Pebble/filters.html) alter a result's output.  
> The number formatting of `simple`, `money` and `percent` are customizable in [the `placeholders:` section of config.yml.](../GitHub/Rankup3/config/Placeholders.html)  

Filter | Description | Example
- | - | -
`percent` | Formats result to be ##.#. Use with `percent` method. | `{{ rank.requirement('money').percent \| percent }}`
`money` | Formats result to be ###,###.##. | `{{ rank.requirement('money').total \| money }}`
`simple` | Formats result to be whole numbers. | `{{ rank.requirement('xp-level').total \| simple }}`

Using filters is recommended for displaying any non-integer number, otherwise the formatting may be too exact (for example, `0.2000000001` or `4.0`). The `simple` filter is recommended for most use cases.
