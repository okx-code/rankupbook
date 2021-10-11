<html>
  <head>
    <meta name="description" content="Reference for provided Pebble Placeholders.">
    <meta name="keywords" content="Rankup, Minecraft, Plugin, Spigot, Prestige">
  </head>
</html>

# Placeholder Engine

## What Is This?

### Text Templating uses [Pebble](./Pebble/templates.html). All Pebble scripting functions and variables are accessible in Rankup 3.12+.

This engine provides many useful scripting features within rankups, prestiges, and locales. By embedding scripts, you can create complex structures inside Rankup which were previously impossible. Pebble placeholders are replacing the legacy placeholders like `{PLAYER}` and `{MONEY}`. You can find those on the [Placeholders](./Placeholders.html#placeholders) page.

## Context Reference

> #### The following examples use spaces between the placeholder and the curly brackets. The spaces are not necessary, but we always include them for better readability. Feel free to omit them.

Rank Placeholder | Next Placeholder | Description
----------- | ----- | -----------
`{{ player }}` | N/A | Username of the player.
`{{ rank.rank }}` | `{{ next.rank }}` | The current rank of the player.
`{{ rank.name }}` | `{{ next.name }}` | The `display-name` for the current rank the player is on.
`{{ rank.from }}` | `{{ next.from }}` | The current prestige of the player.
`{{ rank.to }}` | `{{ next.to }}` | The next prestige of the player.
`{{ rank.index }}` | `{{ next.index }}` | The index within the rankups list. 0 means it is the first rankup..
`{{ rank.done }}` | `{{ next.done }}` | Returns true if all requirements are complete, otherwise false.
`{{ ranks }}` | N/A | A list of all ranks seperated by commas.
`{{ ranks[<index>] }}` | N/A | Similar to `{{ ranks }}` but for a specific rank. `<index>` must be a number.<br>Returns a rank, so you can use `{{ rank }}` methods.
`{{ rank.requirement('<requirement>') }}`<br>`{{rank.req('<requirement>') }} ` | `{{ next.requirement('<requirement>') }}`<br>`{{next.req('<requirement>') }} ` | Get a specific requirement for the rank the player is on.
`{{ rank.requirements[<index>] }}` | `{{ next.requirements[<index>] }}` | Retrieve a requirement by its index.<br>Useful if you have multiple requirements of the same name.<br> `{% rank.requirements %}` [is iterable](./Pebble/Iterable.html).
`{{ seconds }}` | N/A | Total cooldown in seconds before you can rankup again.
`{{ seconds_left }}` | N/A | What's left of the cooldown in seconds before you can rankup again.