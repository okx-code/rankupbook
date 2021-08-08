# Permission Rankup

### What is it?
[`permission-rankup`](https://github.com/okx-code/Rankup3/blob/49942e5497de6da0c5fd20fe4deed2fd49620bc9/src/main/resources/config.yml#L41-L47) is a setting in the [`config.yml`](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml).

### Usecases
- Your permission plugin doesn't (properly) support Vault. 
  - GroupManager.
- Per-Server rankups for BungeeCord servers.
- You don't want to create groups.

### What does it do?
By default, `permission-rankup` is set to `false`. In this case, Rankup will do all the work of checking if the player is on the ladder and moving the player from one group to the next automatically via Vault.

When `permisison-rankup` is set to `true`, Rankup will check if the player is on the ladder by checking the player for the `rankup.rank.<rank>` node. The player will **not** be moved automatically when all requirements are met and they `/rankup`. You will need to use [`commands:`](../Rankups-and-Prestiges/Optionals.md#1-commands) to move the player between groups or permission nodes accordingly.

<details>
	<summary>permission node format: <code>rankup.rank.rank-name</code></summary>
	Example:
	<br>
	<code>rank: Member</code>
	<br>
	permission node: <code>rankup.rank.Member</code>
</details>

### Implementation
> These examples use LuckPerms. Use an equivalent command provided by your permission plugin if different!

In luckperms you have two options for applying the correct permissions:

#### Apply Permissions to the Player
```yaml
starter:
  rank: 'Starter' # assume LP group `default` has `rankup.rank.Starter`
  next: 'Member' # next permission node is 'rankup.rank.Member'
  requirements:
    - 'money 5000'
  commands: # Commands changing permissions on the player directly
    - 'lp user {{player}} permission unset rankup.rank.{{rank.rank}}' # Add extra parameters, this command is universal.
    - 'lp user {{player}} permission set rankup.rank.{{next.rank}}'
```
#### Apply a Group to the Player
```yaml
    # Adding permission groups with the following commands.
    - 'lp user {{player}} parent remove {{rank.rank}}'
    - 'lp user {{player}} parent add {{next.rank}}'
    # The groups must have the permission nodes!
```
