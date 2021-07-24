## If Statements

### What is an `if` statement?

An `if` evaluates a logic statement as either true or false. An example logic statement includes comparison of two values with an operator. If the result is `true`, then it will execute the code within the next block. When the statements evaluates to `false` the `elseif` will be evaluated. Only when all `if` and following `elseif` fail will the `else` code block be executed.

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

```yml
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
