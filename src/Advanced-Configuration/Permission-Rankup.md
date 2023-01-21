<meta name="description" content="Primer and Tutorial for Permission-Rankup!">
<meta name="keywords" content="Rankup, Minecraft, Plugin, Spigot, Prestige">

# [`permission-rankup`](../GitHub/Rankup3/config/Permission-Rankup.html) is a setting in the [`config.yml`](../GitHub/Rankup3/config.html).

### Usecases
- Your permission plugin doesn't (properly) support Vault. 
  - <details><summary>GroupManager.</summary><p>GroupManager doesn't properly support Vault.</p></details>
  - <details><summary>UltraPermissions.</summary><p>UltraPermissions doesn't properly support Vault.</p></details>
- Per-Server rankups for BungeeCord servers.
- You don't want to create groups.

### What does it do?
By default, [`permission-rankup` is set to `false`](../GitHub/Rankup3/config/Permission-Rankup.html). In this case, Rankup will do all the work of checking if the player is on the ladder and moving the player from one group to the next automatically via Vault.

When [`permission-rankup: true`](../GitHub/Rankup3/config/Permission-Rankup.html), Rankup will check if the player is on the ladder by checking the player for the `rankup.rank.<rank>` node. The player will **not** be moved automatically when all requirements are met and they `/rankup`. You will need to use [`commands:`](../Rankups-and-Prestiges/How-to-Rankups.yml.md#1-commands) to move the player between groups or permission nodes accordingly.

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
