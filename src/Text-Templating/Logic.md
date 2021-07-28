# Logic

Pebble supports logic. We'll go through all the operators here.

## Comparisons

Comparisons return a boolean value.

- `==` - Equals
  - `{% if rank.req('money').progress == 1500 %}`<br>True if `rank.req('money').progress` is exactly 1500.<br><br>`equals` is an *alias* for `==`.<br>So<br>`{% if rank.req('money').done equals false %}`<br>And<br>`{% if rank.req('money').done == false %}`<br>Output the same.
- `>=` - Greater than or equal to
  - `{% if rank.req('money').progress >= 1500 %}`<br>True if `rank.req('money').progress` is greater than or equal to 1500.

- `>`  - Greater than
  - `{% if rank.req('money').progress > 1500 %}`<br>True if `rank.req('money').progress` is greater than 1500.

- `<=` - Lesser than or equal to
  - `{% if rank.req('money').progress <= 1500 %}`<br>True if `rank.req('money').progress` is less or equal to 1500.

- `<`  - Lesser than
  - `{% if rank.req('money').progress < 1500 %}`<br>True if `rank.req('money').progress` is less than 1500.

- `!=` - Does not equal
  - `{% if rank.req('money').progress != 1500 %}`<br>True if `rank.req('money').progress` is not 1500.

## And

The `and` logic gate can be used to join together multiple *boolean* expressions. If all the boolean expressions check out, it will execute the code block.

```yml
AndExample:
  rank: 'Intermediate'
  next: 'Advanced'
  display-name: '&8Intermediate'
  requirements:
    - 'money 500000'
    - 'xp-level 50'
  rankup:
    requirements-not-met: |-
      {% if rank.req('money').done equals false and rank.req('xp-level').done equals false %}
      This is the output when BOTH "money" and "xp-level" are not satisfied!
      {% else %}
      This is the output if EITHER one is satisfied!
      {% endif %}
```

## Or

The `or` logic gate can be used to join together multiple *boolean* expressions. If either one of the expressions checks out, it will execute the code block.

```yml
OrExample:
  rank: 'Intermediate'
  next: 'Advanced'
  display-name: '&8Intermediate'
  requirements:
    - 'money 500000'
    - 'xp-level 50'
  rankup:
    requirements-not-met: |-
      {% if rank.req('money').done equals false or rank.req('xp-level').done equals false %}
      This is the output when EITHER "money" or "xp-level" are not satisfied!
      {% else %}
      This is the output if NEITHER one is satisfied!
      {% endif %}
```
