> Text templating is an experimental feature implemented in version 3.12. Only available on the Discord server.

Text templating uses [Pebble](https://pebbletemplates.io/).

## Context Reference

Most of the following values are available as the context, if it makes sense for the message.
<details>
  <summary>Raw Summary</summary>
  <p>
    player: String<br>
    ranks: Rank[] - a list of all ranks<br>
    rank: Rank or Prestige<br>
    next: Rank or Prestige<br>
    seconds: Int<br>
    seconds_left: Int<br>
  </p>
</details>

Placeholder | Type | Description | Example
--- | --- | --- | ---
`{{ player }}` | text<br>(`string`) | Username of the player | "Beep" ranks up, announcement is `{{ player }} ranked up`.<br>Chat says "Beep ranked up".
`{{ rank[] }}` | text<br>(`string`) | A list of all ranks | Ranks are "Guest", "Member", and "Elder".<br>Message is `All ranks are {{ rank[] }}`.<br>Chat says "All ranks are Guest Member Elder".
`{{ rank[<index>] }}` | text<br>(`string`) | Similar to `{{ rank[] }}` but for a specific rank. | Ranks are "Guest", "Member", and "Elder".<br>Message is `Highest rank is {{ rank[2] }}`.<br>Chat says "Highest rank is Elder".
`{{ rank.rank }}` | text<br>(`string`) | The current rank of the player.<br>Works for rankup and prestige messages. | "Beep" is rank "Member". Message is<br>`Your rank is {{ rank.rank }}`.<br>Chat says "Your rank is Member".
`{{ rank.next }}` | text<br>(`string`) | The next rank of the player.<br>Works for rankup and prestige messages. | Beep's next rank is "Elder". Message is<br>`Your next rank is {{ rank.next }}`.<br>Chat says "Your next rank is Elder".
`{{ seconds }}` | number<br>(`int`) | Total cooldown length in seconds for when you can rank up again.
`{{ seconds_left }}` | number<br>(`int`) | Cooldown in seconds for when you can rank up again.

## Types References

Below is a list of types and how you can use them.

#### Rank

<details>
  <summary>Raw Summary</summary>
  <p>
    rank: String - the group name of the rank<br>
    name: String - the display name of the rank<br>
    requirements: Requirement[] - a list of all the rank's requirements<br>
    requirement('name'): Requirement - get the specified requirement by its name<br>
    done: Boolean - true if the player has completed all requirements<br>
    index: Int - Position in list of ranks<br>
  </p>
</details>

String | Placeholder | type | Description | Example
--- | --- | --- | --- | ---
<br> | `{{ rank.rank }}` | string | The group name of the rank the player is in.
<br> | `{{ name.rank }}` | string | The display name of the rank the player is in.
<br> | `{{ requirements[] }}` | array | A full list of requirements for<br>the rank the player is on.
<br> | `{{ requirement('<requirement>') }}` | string | Get a specific requirement for<br>the rank the player is on. | `{{ requirement('money') }}`
`.done` | | boolean | Amount of a requirement done | `{{ requirement('money').done }}`
<br> | `{{ rank[<index>] }}` | int | Position in a list of ranks | `{{ rank[2] }}`

#### Prestige

Contains all fields from ranks

<details>
  <summary>Raw Summary</summary>
  <p>
    from: String<br>
    to: String
  </p>
</details>

Placeholder | type | Description
--- | --- | ---
`{{ from }}` | string | Rank the player prestiges from.
`{{ to }}` | string | Rank the player prestiges to.

#### Requirement

<details>
  <summary>Raw Summary</summary>
  <p>
    name: String<br>
    done: Boolean<br>
    total: Double<br>
    progress: Double<br>
    remaining: Double - equal to total minus progress<br>
    percent: Double - goes from 0 to 1, for actual percent do {{ (requirement.percent * 100) }}
  </p>
</details>

String | type | Description | Example
--- | --- | --- | --- 
`done` | boolean | True or false depending on if the requirement is complete. | `{{ rank.requirement('money').done }}`
`total` | double | Displays total amount required. | `{{ rank.requirement('money').total }}`
`progress` | double | Amount done of a requirement | `{{ rank.requirement('money').progress }}`
`remaining` | double | Amount left of a requirement | `{{ rank.requirement('money').remaining }}`
`percent` | double | Goes from 0 to 1. For actual percentage multiply by 100 | `{{ rank.requirement('money').percent }}`
