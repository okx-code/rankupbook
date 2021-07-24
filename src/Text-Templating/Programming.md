# What Is This?

As you read in the previous page, Rankup's placeholder engine works on a Java templating engine called Pebble. This engine provides many useful features which are accessible to you. With this you can create many things withing Rankup which were previously impossible, like IF statements,

## IF Statements

### what is an IF statement?

An IF statement compares two values with eachother using an operator. If the result is `true`, then it will execute the code within a certain codeblock.

An example
```yml
IfExample:
  rank: 'Intermediate'
  next: 'Advanced'
  display-name: '&dIntermediate'
  requirements:
    - 'money 175000'
    - 'xp-level 40'
  rankup:
    requirements-not-met: |-
      {% if rank.req('money').done == true %}
      Great job, {{ player }}! You've gathered all {{ rank.req('money').total | simple }} coins!
      {% else %}
      Oh no! {{ player }}, you don't have enough money! You need {{ rank.req('money').remaining | simple }} more coins!
      {% endif %}
      
      {% if rank.req('xp-level').done == true %}
      The warden will be very pleased with your {{ rank.req('xp-level').total | simple }} XP levels, I'm sure of it!
      {% else %}
      Quick! You must gather {{ rank.req('xp-level').remaining | simple }} more XP levels or the warden will have my head!
      {% endif%}
```

You can put anything inside an IF statement, even another IF statement!

### Else If Statement

This is for when you want to go through several comparisons inside a single IF statement.

```
ElseIfExample:
  rank: 'Intermediate'
  next: 'Advanced'
  display-name: '&dIntermediate'
  requirements:
    - 'money 175000'
  rankup:
    requirements-not-met: |-
      {% if rank.req('money').done == true %}
      &5{{ rank.req('money').total | simple }}
      {% elseif rank.req('money').percent >= 0.5 %}
      &d{{ rank.req('money').progress | simple }}
      {% else %}
      &b{{ rank.req('money').progress | simple }}
      {% endif %}
```

## Set

The `set` tag allows you to define a variable. You can practically create your own placeholders with it!

Notable things:
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

