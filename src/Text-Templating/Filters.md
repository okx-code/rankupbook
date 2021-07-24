## Filters

Filters serve to format the original result to fit your purpose better. The following filters were custom-made for Rankup.
> Find the built-in filters [here](https://pebbletemplates.io/wiki/filter/abbreviate/).

Filters are ways to convert numbers into more readable options. Rankup provides three filters, `simple`, `money` and `percent`. These use the number formatting found in the `placeholders` section of Rankup's `config.yml`.

You can use filters with a pipe symbol `|` and then the name of the filter. Here are some examples:

Filter | Description | Example
------ | ----------- | -------
`percent` | Formats result to be ##.#. Use with `percent` method. | `{{ rank.requirement('money').percent \| percent }}`
`money` | Formats result to be ###,###.##. | `{{ rank.requirement('money').total \| money }}`
`simple` | Formats result to be whole numbers. | `{{ rank.requirement('xp-level').total \| simple }}`

Using filters is recommended for displaying any non-integer number to a player, otherwise the formatting may not be as desired (for example you can get something like 0.2000000001 or 4.0). The `simple` filter is recommended for most use cases.