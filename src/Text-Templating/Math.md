# Math

You can do math inside placeholders!

Things to note:
  - Order of operations applies.
  - You can use variables as long as they're numbers.
    - This means you can do math with Rankup's placeholders!

Quick refresher on operators:
  - `+` - Add
  - `-` - Subtract
  - `*` - Multiply
  - `/` - Divide
  - `%` - Remainder

```yml
{% set num1 = 5 %}
{{ 5 * (num1 + 1) }}
{{ rank.req('money').progress * num1 | simple }}
```
