# Permission Rankup

> ### This page assumes that you are using LuckPerms. Use the equivalent of the command provided by the plugin you use!

## What is it?
[`permission-rankup`](https://github.com/okx-code/Rankup3/blob/49942e5497de6da0c5fd20fe4deed2fd49620bc9/src/main/resources/config.yml#L41-L47) is a setting in the [`config.yml`](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml) for when either the permission plugin you're using doesn't support Vault correctly, you want global ranks on BungeeCord or you can't or don't want to create the groups.

## What does it do?
> By default, `permission-rankup` is set to `false`.

When `permission-rankup` is set to `false`, Rankup will do all the work of moving the player from one group to the next automatically.

When `permisison-rankup` is set to `true`, Rankup will not take any action appart from checking if the player meets the requirements for the rank the player is at. The player will **not** be moved. You will need to manually add commands to move the player between groups or permission nodes accordingly.

## How does it work?

Now that you know what Rankup checks for when `permission-rankup` is set to `true`, we can continue onto how to use it and set it up.
#### Necessary information
- each rank has its own permission node Rankup will check for.
  <details><summary>permission node format: <code>rankup.rank.rank-name</code>.</summary>rank: <code>Member</code><br>permission node: <code>rankup.rank.Member</code></details>
- how to use [**commands**](../Rankups-and-Prestiges/Optionals.md#1-commands).

### Implementation
> ##### Example will use permissions.
Assume that LuckPerms group `default` has permission node `rankup.rank.Starter`
```yaml
starter:
  rank: 'Starter' # permission node 'rankup.rank.Starter'
  next: 'Member' # permission node 'rankup.rank.Member'
  requirements:
    - 'money 5000'
  commands:
    - 'lp user {{player}} permission unset rankup.rank.{{rank.rank}}' # Add extra parameters, this command is universal.
    - 'lp user {{player}} permission set rankup.rank.{{next.rank}}'
```
For adding and removing groups use the following commands instead.
> #### The groups themselves need to have the permission nodes!
```yaml
    - 'lp user {{player}} parent remove {{rank.rank}}'
    - 'lp user {{player}} parent add {{next.rank}}'
```
