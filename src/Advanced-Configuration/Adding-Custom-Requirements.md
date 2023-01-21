<meta name="description" content="Tutorial for adding custom requirements to a rankup using PAPI!">
<meta name="keywords" content="Rankup, Minecraft, Plugin, Spigot, Prestige">

# Adding PAPI Requirements

It's possible to use a PAPI placeholder as a requirement with the format `- 'placeholder <PAPI Placeholder>'`.

```yaml
example:
  rank: 'currentRank'
  next: 'nextRank'
  requirements: # %statistic_hours_played% is from the PAPI ecloud via /papi ecloud download Statistic
    - 'placeholder %statistic_hours_played% >= 12'
  rankup:
    requirements-not-met: |-
      You need:
      {{ rank.requirement('placeholder', 'statistic_hours_played').total | simple }} hours of playtime.
      to rank up to {{ next.rank }}!
```

#### **IMPORTANT:** Make sure the plugin you want to use supports **PlaceholderAPI** (PAPI), if it doesn't you won't be able to use it.

> Placeholders can be found from the [PAPI github wiki/ecloud](../GitHub/PAPI/Placeholders.html). The placeholder needs to output a **raw number**.  
> That means no periods, dots, or commas.  
> For example, if the placeholder outputs it like this it won't work:  
> `1000 = 1,000 or 1000.00`  
> Only __whole, unformatted numbers__ will work.  
> Now onto the syntax. This is the template:  

###### Template
```yaml
RankName:
  rank: 'currentRank'
  next: 'nextRank'
  requirements:
    - 'placeholder <placeholder> <operation> <number>'
```
__Important things to note:__
- when using a placeholder, write `placeholder` in front of it so Rankup knows it's a placeholder.
- `<placeholder>` is where your placeholder goes. Again, unformatted numbers only.
- `<operation>` is where you specify what should be checked for. See below for a list of operations.
- `<number>` is the number that will be used by the `operation`.

### Operations

> All of the following operations will be explained assuming the syntax above is used.  
> `>` greater than  
> `<` smaller than  
> `>=` equal to or greater than (**recommended**)  
> `<=` smaller or equal to  
> `=` equal to/matches  
> `==` exact match (not recommended)  

##### An Example Operation:
```yaml
RankName:
  rank: 'currentRank'
  next: 'nextRank'
  requirements:
    - 'placeholder %statistic_hours_since_death% >= 5'
```

> Need more customization? If you can write Java, see [Developers](../For-Developers.md)
