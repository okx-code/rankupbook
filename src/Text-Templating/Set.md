## Set

The `set` tag allows you to define a variable. You can practically create your own placeholders with it!

Notable things:
- You should NOT use a variable name provided by Rankup.
- You can redefine something if you use the same variable name.
- You can show the variable as a placeholder if you encase it in curly brackets.

```yml
SetExample:
  rank: 'Intermediate'
  next: 'Advanced'
  display-name: '&dIntermediate'
  requirements:
    - 'money 175000'
  rankup:
    requirements-not-met: |-
      {% if rank.req('money').done == true %}
      {% set moneyColor = '&5' %}
      {% elseif rank.req('money').percent >= 0.5 %}
      {% set moneyColor = '&d' %}
      {% else %}
      {% set moneyColor = '&b' %}
      {% endif %}
      
      {{ moneyColor }}{{ rank.req('money').progress | simple }}
```