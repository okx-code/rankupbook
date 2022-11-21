<title>Pebble Snippets - Official Rankup Wiki</title>
<meta name="description" content="Handy bits of PebbleScript for specific scenarios">

# Pebble Snippets

---

#### What Does It Do?
It adds all previous requirements of the same type together and subtracts them from your current rank's requirement.

#### Reasoning
Some requirements are based on player statistics. This means that if you want to use a requirement multiple times you'll have to assign a value high enough so that your players will still have to "complete" the actual requirement.

With this Snippet, you still have to assign a high value, but your players will only ever see the difference between the values you've given the requirements.

###### The Snippet
```yaml
      {% set tmk = 'total-mob-kills' %}{% set indexTotal = 0 %}{% set reqIncrement = 0 %}
      {% for i in ranks %}{% if indexTotal < rank.index %}
      {% set indexTotal = indexTotal + 1 %}{% set reqIncrement = reqIncrement + ranks[rank.index - indexTotal].req(tmk).total %}
      {% endif %}{% endfor %}{{(rank.req(tmk).total-reqIncrement)|simple}}
```

#### Usage & Modification
The Snippet is using the `total-mob-kills` requirement, but you can change that easily by simply replacing the requirement in the Snippet to whatever you need. As it stands, you can simply put it at the top of any message you'd like to display the relative amount on and it'll work.

You only need to paste the Snippet once for it to work inside the message. Once pasted, you can use the `reqIncrement` (**Case Sensitive!**) anywhere.

---