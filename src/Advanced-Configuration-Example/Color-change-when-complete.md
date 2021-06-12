# Change Requirement Chat Color When Completed!

![](https://i.imgur.com/djubbyW.png)

The config that you see above. all in the `rankups.yml`!
```yaml
    requirements-not-met: |-
      &4&m+                                       +
      &cYou need
      &c- {{rank.requirement('money').done ? '&d' : '&c'}}${{rank.requirement('money').progress | money}} / ${{rank.requirement('money').total | money}}
      
      &cto rankup from &7&l%rankup_current_rank%&r&c to &e&l%rankup_next_rank%&r&c!
      &4&m+                                       +
```

## Let's break it down:
- `{{rank.requirement('money').done ? '&d' : '&c'}}`
  - `{{rank.requirement('money)` Specifies the target.
  -  `.done` Is a _boolean_, Meaning it outputs `true` or `false`. In Rankup, it outputs `true` if the requirement is fulfilled.
  -  `? '&d' : &c` This is the "picker" if the _boolean_ (`.done`) returns `true`, it uses `'&d'` and if `false` then `'&c'`.
  -  > Recap: Placeholder checks if requirement is done or not and outputs the appropriate field (`'&d'` or `'&c'`) accordingly.
- `{{rank.requirement('money').progress | money}}`
  - Amount player has.
- `{{rank.requirement('money').total | money}}`
  - The total amount required.

### The important bit
`{{rank.requirement('money').done ? '&d' : '&c'}}`

### How to change...
- The color when completed:
  - Change the `'&d'`, Hex codes work.
- The color when incomplete:
  - Change the `'&c'`, Hex codes work.
- The requirement:
  - Change `'money'`.
