## Using PAPI in Requirements
As mentioned in the **[Configuration Example](https://github.com/okx-code/Rankup3/wiki/Configuration-Example)**, Rankup supports PAPI (PlaceholderAPI) which let's you use placeholders as requirements. It's a lot easier than it sounds, so here's an example. All PAPI placeholders can be found on their **[wiki](https://github.com/PlaceholderAPI/PlaceholderAPI/wiki/Placeholders)**.
 
**IMPORTANT:** You need to download the expansion pack. If it says "NO DOWNLOAD COMMAND" then it's hardcoded into the plugin you're using and it will work regardless, Like Rankup.
 
We'll go with how many times you've jumped. We will be building on what we had after following the **[Configuration Example](https://github.com/okx-code/Rankup3/wiki/Configuration-Example)**
 
```yaml
beginner:
  rank: beginner
  next: member
  requirements:
  - 'xp-level 5'
  - 'placeholder %statistic_jump% >= 50'
  rankup:
    requirements-not-met: "&cYou have {AMOUNT_DONE xp-level}, and need {AMOUNT xp-level} xp levels to rankup!"
    gui:
      rankup:
        material: EMERALD_BLOCK
        index: 0-3
        name: '&a&lConfirm'
        lore: |-
          &6Rankup to &b{RANK}
          &eCosts {AMOUNT xp-level} xp levels.
```
 
As you can see, we've added a new requirement: `- 'placeholder %statistic_jump% >= 50'`, now let's analyze it.
* The `placeholder` part in front is necessary for Rankup to recognize that it's a placeholder.
* The `%statistic_jump%` part is the placeholder itself. Rankup will read it as how many times you've jumped thanks to PAPI.
* the `>= 50` part means that it should be `equal or greater than 50`. Basically 50 or more.
