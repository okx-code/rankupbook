<html>
  <head>
    <meta name="description" content="Reference for rankup's provided Pebble Formatting suffixes and filters.">
    <meta name="keywords" content="Rankup, Minecraft, Plugin, Spigot, Prestige">
  </head>
</html>

## Requirements

Methods tell the placeholder engine what part of the result you want.

> Only methods used to display a value regarding a requirement are listed below. For more or different methods, refer to the [Placeholder Engine](../Text-Templating.md) page.

| Method | Description | Example |
| --- | --- | --- |
`done` | True or false depending on if the requirement is complete. | <code>{{ rank.requirement('money').done }}</code>
`total` | Displays total amount required. | <code>{{ rank.requirement('money').total }}</code>
`progress` | Amount done of a requirement. | <code>{{ rank.requirement('money').progress }}</code>
`remaining` | Amount left of a requirement. | <code>{{ rank.requirement('money').remaining }}</code>
`percent` | Goes from 0 to 100. | <code>{{ rank.requirement('money').percent }}</code>
`quotient` | Like percent, but goes from 0 to 1. | <code>{{ rank.requirement('money').quotient }}</code>

## Filters

> The pipe symbol `|` and the filter name will apply it.  
> [Filters](../Pebble/filters.html) alter a result's output.  
> The number formatting of `simple`, `money` and `percent` are customizable in [the `placeholders:` section of config.yml.](../GitHub/Rankup3/config/Placeholders.html)  

Filter | Description | Example
--- | --- | ---
`simple` | Formats result to be whole numbers. | <code>{{ rank.requirement('xp-level').total \| simple }}</code>
`percent` | Formats result to be ##.#. Use with `percent` method. | <code>{{ rank.requirement('money').percent \| percent }}</code>
`money` | Formats result to be ###,###.##. | <code>{{ rank.requirement('money').total \| money }}</code>
`shortmoney` | Formats result to a letter | <code>{{rank.requirement('money').total \| shortmoney }}</code>


Using filters is recommended for displaying any non-integer number, otherwise the formatting may be too exact (for example, `0.2000000001` or `4.0`). The `simple` filter is recommended for most use cases.
