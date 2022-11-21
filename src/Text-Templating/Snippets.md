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

## Playtime in Words

### What Does It Do?
It converts the `playtime-minutes` requirement to a string of words, similar to the `/playtime` command from Essentials.  
Ex: `1 Millennia 2 Centuries 3 Decades 4 Olympiads 5 Years 6 Months 7 Days 8 Hours 9 minutes`.

#### Reasoning
No simple date/time formatting is readily available with this requirement since it is only an integer which counts up as the vanilla playtime statistic increases. Instead, some math should be done to make this number recognizable to players on your server.

##### The Snippet
```
      requirements-not-met: |
        {% set playtime = rank.req('playtime-minutes') %}
        {% set titles = ["Millennia", "Centuries", "Decades", "Olympiads", "Years", "Months", "Days", "Hours", "Minutes"] %}
        {% set times = [525960000, 52596000, 5259600, 2103840, 525960, 43830, 1440, 60, 1] %}
          &8- &d{{playtime.total | simple}} &eTotal Required Minutes Played
          &8- &d{{playtime.progress | simple}} &eCurrent Minutes Played for {{player}}
        {% set formed = '' %}
        {% set total = playtime.total %}
        {% for mins in times %}
        {% if total >= mins %}
        {% set formed = formed + ((total / mins) | numberformat("00")) + ' ' + titles.get(loop.index) + (loop.last ? '' : ' ') %}
        {% set total = total % mins %}
        {% elseif mins == 1 %}{% set formed = formed + '00' %}
        {% endif %}
        {% endfor %}
          &8- &d{{ formed }} &eFormatted Total Required Time Played
        {% set formed = '' %}
        {% set total = playtime.progress %}
        {% for mins in times %}
        {% if total >= mins %}
        {% set formed = formed + ((total / mins) | numberformat("00")) + ' ' + titles.get(loop.index) + (loop.last ? '' : ' ') %}
        {% set total = total % mins %}
        {% elseif mins == 1 %}{% set formed = formed + '00' %}
        {% endif %}
        {% endfor %}
          &8- &d{{ formed }} &eFormatted Current Time Played for {{player}}
```

#### Usage & Modification

The `titles` list must be localized to appropriate strings for your units of time manually.  
The `times` list was created using the [wikipedia 'Unit of time' list](https://en.wikipedia.org/wiki/Unit_of_time#List).  
Convert any unit of time to minutes, add it to the list of times and provide it a corresponding unit title in first list. Many potentially unnecessary units were included in the list above to enable direct replacement.