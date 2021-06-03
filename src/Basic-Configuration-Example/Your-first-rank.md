# Your First Rank
The first time you start your server **with Rankup installed** the default **[rankups.yml](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/rankups.yml)**, **[config.yml](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml)**, and **[locale](https://github.com/okx-code/Rankup3/tree/master/src/main/resources/locale)** will generate like **[this](https://github.com/okx-code/Rankup3/tree/master/src/main/resources)**. Stop your server once the plugins have loaded. The **[rankups.yml](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/rankups.yml)** file is where you will add your ranks to. We recommend you take your time to read through it and all the comments.
#### [See this FAQ section before continuing the tutorial!](../Core-Files/FAQ.md#YAML-Questions)
## Starting to Format
* [Each rankup needs a `heading:`, `rank:`, `next:`, and `requirements:` to be valid.](../Rankups-and-prestiges/How-to-rankups.yml.md#these-are-the-4-required-sections-in-the-rankupsyml-file-necessary-for-a-rankup-to-be-considered-valid-individually)
* You can only have one starter rank as multiple _"roots"_ aren't possible. Multiple roots will cause the following error:
`[Server] ERROR [Rankup] Multiple root rankup nodes detected (a root rankup nodes is a rankup that does not have anything that ranks up to it). This may lead to inconsistent behaviour.`
* The last rankup of a ladder (all the ranks) should refer to the last rank in `next:`. This rank should not be the `rank:` of any other step.
* The prior also applies to prestiges' `rank:` and `next:`.  
**IMPORTANT:** If you change the configuration file while the server is running, some settings may not be applied until the next restart. However, you can safely work on the rankups.yml, prestiges.yml, and locale files while the server is running and use the command `/rankup3 reload` or `/pru reload` to apply saved changes from those files. **Reloading Rankup with the command will not cause issues**. Errors may occur while reloading when the files contain [invalid user-generated YAML code](../Core-Files/FAQ.md#YAML-Questions).  

**[LuckPerms](https://www.spigotmc.org/resources/luckperms-an-advanced-permissions-plugin.28140/)** is strongly recommended and will be used throughout the below examples to manage our groups.

### First Example
This example will provide the basis for the entire tutorial.
```yaml
defaultToMember:
  rank: 'default'
  next: 'member'
  requirements:
    - 'xp-level 5' # the indentation of 2 spaces is very important
    # YAML files are whitespace and format sensitive.
```
#### First Example Line By Line Breakdown:
1. [`defaultToMember:`](../Rankups-and-prestiges/How-to-rankups.yml.md#1-heading) Indicates the subsequent indendented subsections are part of a rankup step on the ladder. The text `defaultToMember` must only be unique from all other `heading:` sections.
2. [`rank: 'default'`](../Rankups-and-prestiges/How-to-rankups.yml.md#2-rank) Sets the group players must be in to be able to use this rankup step from "default". (`default` is our example current group in `{{ rank.rank }}`)
3. [`next: 'member'`](../Rankups-and-prestiges/How-to-rankups.yml.md#3-next) Sets the group assigned to the player when they've met the requirements and use `/rankup` to complete this rankup to "member". (`'member'` is our example next group in `{{ next.rank }}`)
4. [`requirements:`](../Rankups-and-prestiges/How-to-rankups.yml.md#4-requirements) This begins the list of requirements section.
5. [`- xp-level 5`](../Core-Files/List-of-Requirements.md) This example assumes the only requirement we want for a player to rankup is 5 xp levels as deducted (as a sort of payment). If we wanted to let players keep their xp levels when ranking up, we could check how many xp levels they _have_ with `xp-levelh` (compare) instead of `xp-level` (deduct). Rankup will only take the given number of any requirement (`xp-level 5` here) away once a player successfully ranks up. We only used one requirement for this example, but you can have many different kinds of **[requirements](../Core-Files/List-of-Requirements.md)** by following the above format.  

Follow the links provided in 1 through 5 to see more detailed descriptions of these sections.  

After replacing the default example in rankups.yml with the [first example](../Basic-Configuration-Example/Your-first-rank.md#first-example), now we're ready to `/pru reload` or `/rankup3 reload` to apply the changes while the server is running.
###### The plugin used to be called PrisonRankup, which is why [pru is still an alias](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/plugin.yml#L13-L16).
## Group Management
Assuming all users start with the 'default' group, anyone should be able to immediately see the rankup as `Current` or in-progress!  
Before trying to complete the rankup, let's create the group `member`, otherwise Rankup won't change the player's groups.  
To create our group we'll be using the **[LuckPerms creategroup](https://luckperms.net/wiki/General-Commands#lp-creategroup-name-weight-displayname)** command.
```
/lp creategroup member
```
Now, make sure your primary group in LP is `default` and then type /rankup to rankup the ladder to member.  
Let's say you **don't have** the xp levels needed. It will say in chat:
```
You need {{ rank.requirement('money').total | money }} money to rankup.
```
You might think something went wrong, but that's not the case! This is the default message when you don't meet some requirements.
