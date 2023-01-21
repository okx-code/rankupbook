<meta name="description" content="Tutorial on making progress bars for rankup requirements with Pebble!">
<meta name="keywords" content="Rankup, Minecraft, Plugin, Spigot, Prestige">

# Pebble Progress Bars

## Warning:
This tutorial is not final.  
This warning will be removed when completely validated.

### Important Notes:
- You can use any requirement!
- You can simply copy, paste, and edit to your preference.
- Doesn't require **[PlaceholderAPI](../Spigot/PAPI.html)** ([see PAPI Progress Bars](./PAPI-Progress-Bars.md)).

## Pebble Progress Bar Example
```yaml
      lore: |-
        &8&m       &a&l<Requires>&8&m       
        &8- &eAccrued §d{{rank.req('xp-levelh').total}}&e Levels
        &8- &d¤{{rank.req('money').total | money}}&e payment
        {% set requirement = rank.req('money') %}
        {% set size = 10 %}
        {% set Lcolor = "&d" %}
        {% set Rcolor = "&3" %}
        {% set Lbar = "|" %}
        {% set Rbar = "|" %}
        {% set bar = "" %}
        {% for i in range(1, size * requirement.quotient) %}{% set bar = bar + Lbar %}{% endfor %}
        {% set bar = Lcolor + bar %}
        {% if requirement.done == false %}
        {% set bar = bar + Rcolor %}
        {% for i in range(1, size * (1 - requirement.quotient)) %}{% set bar = bar + Rbar %}{% endfor %}
        {% endif %}
        &8- &eProgress &8[{{bar}}&8]
```

### Walkthrough
1. Start with the `lore:` tag within any of the three rankup stages in the `ranksgui:`.
   - Note: this can also be used in the subsections of the `list:` if using text for `/ranks`.
2. Add `|` for simple and readable multi-line text in your file.
3. Prepare your rankup step's description with formatting like
`&8&m       &a&l<Requires>&8&m       `
4. Incorporate additional lines for other requirements.
5. Insert the pebble templating before wherever the progress bar goes.
#### Templating
```yaml
        {% set requirement = rank.req('money') %}
        {% set size = 10 %}
        {% set Lcolor = "&d" %}
        {% set Rcolor = "&3" %}
        {% set Lbar = "|" %}
        {% set Rbar = "|" %}
        {% set bar = "" %}
        {% for i in range(1, size * requirement.quotient) %}{% set bar = bar + Lbar %}{% endfor %}
        {% set bar = Lcolor + bar %}
        {% if requirement.done == false %}
        {% set bar = bar + Rcolor %}
        {% for i in range(1, size * (1 - requirement.quotient)) %}{% set bar = bar + Rbar %}{% endfor %}
        {% endif %}
```

6. This templating will create a `{{bar}}` placeholder which can be used after the final line of the template.
7. Put formatting around the bar like:  
```yaml
        &8- &eProgress &8[{{bar}}&8]
```

#### Customizing
```yaml
        {% set requirement = rank.req('money') %}
        {% set size = 10 %}
        {% set Lcolor = "&d" %}
        {% set Rcolor = "&3" %}
        {% set Lbar = "|" %}
        {% set Rbar = "|" %}
```
- Change the `requirement` to get a different requirement's progress.
   - Example: `rank.req('xplevelh')`
   - Note: No requirement suffix like `.total`, `.progress`, or `.quotient` should be used. Output is already handled.
- Increase or decrease the `size` to expand or shrink the progress bar.
- Edit the color codes in `Lcolor` and `Rcolor` to your liking.
- Use different `Lbar` and `Rbar` to alter the progress bar's left and right text segments.