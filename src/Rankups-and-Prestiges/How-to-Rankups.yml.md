# How To `Rankups`  
## Each `heading:` in rankups.yml defines a Rankup from the current `rank:` group to the `next:` group which has some `requirements:`.  
### These are the **4 required sections** in the rankups.yml file necessary for a Rankup to be considered valid individually.  
### 1. `heading:`
Each heading is "a name in the configuration section" and holds **all** of the subsections for each distinct rankup/prestige.  
Since you must name each step to start a new rankup/prestige, headings are required.  
However, the heading is considered `completely unused` because it is never seen reproduced in any message text unless it's a console error.  
The step's name is unimportant, but **must be unique from every other heading**. If two headings have the same name, only one is used, typically the first.  
**An important note**: headings may be named anything, not just "heading".  
Throughout the wiki various heading names are used for different examples.  
### 2. `rank:`
`rank:` defines the permission group a player must currently have to access this rankup, is mandatory in all Rankups **and Prestiges** except for the first prestige, and provides the placeholder `{{ rank.rank }}`.
### 3. `next:`
`next:` defines the permission group a player will move to after completing the rankup, is mandatory in all Rankups **and Prestiges**, and provides the placeholder `{{ next.rank }}`.

The permission groups specified in `rank:` and `next:` should all use the name of the groups provided to Vault by your permission manager. For example, in LuckPerms the `'<name>'` of the group's `displayname.<name>` should be used in place of its internal name unless the display name/node isn't present.  
Do **NOT** `rank: 'displayname.<name>'`. Use `rank: '<name>'` exactly (case-sensitive) instead of the group's name (like the luckperms `default` group). This means they should be text (alpha-numeric with no special symbols nor unicode). 

If you are using [`permission-rankup: true`](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml#L41-L47) you should still avoid special symbols and/or unicode in these fields, as they may interfere with other plugins using vault.
### 4. `requirements:`
The `requirements:` section defines a list of required parameters the player needs to satify in order to move up the ladder (Rankup or Prestige) from *rank* to *next*.  
The list of requirements can be disabled with `requirements: []`.  
A requirement in the list can be any one or more from [The List of Requirements](../List-of-Requirements.md#list).  
#### An example of the minimum required fields with a default config.yml and non-empty requirements:
```yaml
# text following a "# " is a comment in yaml
heading: # "heading" is unused and could be named differently
  rank: first # the permission group required-to and removed-post completion
  next: last # the permission group assigned on completion
  requirements: # things other than `rank:` required for completion
    - 'money 0' # any requirement
```
Requirements are in the format `'requirement-name value'`.  
Some requirements support sub-requirements, and can be used like `requirement-name sub-requirement value`.  
For example: `'mob-kills skeleton 100'`.  

Requirements may also be deductible, which means the player's parameters will be deducted upon completion.  
All payable/deductible requirements may be made non-deductible by adding the letter *h* to the end of the requirement name.  
For example: `money` deducts the subsequent amount while `moneyh` only checks the requirement was met.
