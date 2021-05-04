> Text templating is an experimental feature implemented in version 3.12. Only available on the Discord server.

Text templating uses [Pebble](https://pebbletemplates.io/).


## Context Reference

Most of the following values are available as the context, if it makes sense for the message.

    player: String
    ranks: Rank[] - a list of all ranks
    rank: Rank or Prestige
    next: Rank or Prestige
    seconds: Int
    seconds_left: Int

## Types Reference

Below is a list of types and how you can use them.

#### Rank

    rank: String - the group name of the rank
    name: String - the display name of the rank
    requirements: Requirement[] - a list of all the rank's requirements
    requirement('name'): Requirement - get the specified requirement by its name
    done: Boolean - true if the player has completed all requirements
    index: Int - Position in list of ranks

#### Prestige
Contains all fields from ranks

     from: String
     to: String

#### Requirement

    name: String
    done: Boolean
    total: Double
    progress: Double
    remaining: Double - equal to total minus progress
    percent: Double - goes from 0 to 1, for actual percent do {{ (requirement.percent * 100) }}
