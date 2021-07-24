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