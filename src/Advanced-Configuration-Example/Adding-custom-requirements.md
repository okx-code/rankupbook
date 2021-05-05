# Adding Custom Requirements

> Need more customization? If you can write Java, see [Developers](../Core-Files/For-Developers.md)

#### **IMPORTANT:** Make sure the plugin you want to use supports **PlaceholderAPI** (PAPI), if it doesn't you won't be able to use it.

First of all, you'll need a placeholder. It needs to output a **raw number**. That means that there can't be any periods/dots or comma's mixed in there.  
For example, if the placeholder outputs it like this it won't work:

`1000 = 1,000 or 1000.00`

Only __whole, unformatted numbers__ will work.

Now onto the syntax. This is the template:
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
All of the following operations will be explained assuming the syntax above is used.

`>` greater than  
`<` smaller than  
`>=` equal to or greater than (**recommended**)  
`<=` smaller or equal to  
`=` equal to/matches  
`==` exact match (not recommended)  

##### An Example Operation:
```yaml
RankName:
  rank: 'currentRank'
  next: 'nextRank'
  requirements:
    - 'placeholder %statistic_hours_since_death% >= 5'
```
