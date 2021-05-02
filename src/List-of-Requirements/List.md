# List

**S means "supports sub-requirements?". D means "is deductible?".**

<table style="width:100%">
  <tr>
    <th>Name</th>
    <th>Format</th>
    <th>S</th>
    <th>D</th>
    <th>Description</th>
    <th>Example</th>
  </tr>
  <tr>
    <td>`money`</td>
    <td>number</td>
    <td>no</td>
    <td>yes</td>
    <td>Checks the player's balance and takes the specified amount when ranking up.</td>
    <td>`money 1000`</td>
  </tr>
  <tr>
    <td>`moneyh`</td>
    <td>number</td>
    <td>no</td>
    <td>no</td>
    <td>Checks the player's balance but does not take the money.</td>
    <td>`moneyh 10000`</td>
  </tr>
  <tr>
    <td>`xp-level`</td>
    <td>number</td>
    <td>no</td>
    <td>yes</td>
    <td>Checks the player's xp-levels for the specified amount and takes it.</td>
    <td>`xp-level 30`</td>
  </tr>
  <tr>
    <td>`xp-level`</td>
    <td>number</td>
    <td>no</td>
    <td>no</td>
    <td>Checks the player's xp-levels for the specified amount but does not take them.</td>
    <td>`xp-level 50`</td>
  </tr>
  <tr>
    <td>`playtime-minutes`</td>
    <td>number</td>
    <td>no</td>
    <td>no</td>
    <td>How long a player has been online, in minutes (uses the Minecraft statistic).</td>
    <td>`playtime-minutes 120`</td>
  </tr>
  <tr>
    <td>`group`</td>
    <td>text</td>
    <td>no</td>
    <td>no</td>
    <td>Requires a player to be in at least one of a list of groups, separated by spaces.</td>
    <td>`group vip mvp`</td>
  </tr>
  <tr>
    <td>`permission`</td>
    <td>text</td>
    <td>no</td>
    <td>no</td>
    <td>Requires player to have at least one of a list of permissions, separated by spaces.</td>
    <td>`permission permission.one permission.two`</td>
  </tr>
  <tr>
    <td>`world`</td>
    <td>text</td>
    <td>no</td>
    <td>no</td>
    <td>Requires a player to be in any of the worlds listed, separated by spaces.</td>
    <td>`world my_world_nether my_world_the_end`</td>
  </tr>
  <tr>
    <td>`player-kills`</td>
    <td>number</td>
    <td>no</td>
    <td>no</td>
    <td>Players killed. Uses the Minecraft statistic.</td>
    <td>`player-kills 15`</td>
  </tr>
  <tr>
    <td>`total-mob-kills`</td>
    <td>number</td>
    <td>no</td>
    <td>no</td>
    <td>The total amount of mob kills a player has</td>
    <td>`total-mob-kills 500`</td>
  </tr>
  <tr>
    <td>`mob-kills`</td>
    <td>number</td>
    <td>yes</td>
    <td>no</td>
    <td><a href="https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/package-summary.html">Mobs</a>
 of the specified type killed. Uses the Minecraft statistic.</td>
    <td>`mob-kills Skeleton 100`</td>
  </tr>
  <tr>
    <td>`item`</td>
    <td>number</td>
    <td>yes</td>
    <td>yes</td>
    <td>The amount of <a href="https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html">items</a> a player currently has</td>
    <td>`item DIAMOND 64`</td>
  </tr>
  <tr>
    <td>`itemh`</td>
    <td>number</td>
    <td>yes</td>
    <td>no</td>
    <td>As prior, but does not deduct <a href="https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html">items</a></td>
    <td>`itemh GLASS 64`</td>
  </tr>
  <tr>
    <td>`use-item`</td>
    <td>number</td>
    <td>yes</td>
    <td>no</td>
    <td>The amount of times a player has used an <a href="https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html">item</a></td>
    <td>`use-item DIAMOND_SWORD 200`</td>
  </tr>
  <tr>
    <td>`block-break`</td>
    <td>number</td>
    <td>yes</td>
    <td>no</td>
    <td>The amount of times a player has broken a <a href="https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html">block</a></td>
    <td>`block-break STONE 1000`</td>
  </tr>
  <tr>
    <td>`craft-item`</td>
    <td>number</td>
    <td>yes</td>
    <td>no</td>
    <td>The amount of times a player has crafted an <a href="https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html">item</a></td>
    <td>`craft-item STONE_BRICKS 256`</td>
  </tr>
  <tr>
    <td>`advancement`</td>
    <td>number</td>
    <td>no</td>
    <td>no</td>
    <td>Checks for a specific Minecraft <a href="https://minecraft.fandom.com/wiki/Advancement#List_of_advancements">advancement</a></td>
    <td>`advancement story/obtain_armor`</td>
  </tr>
</table>
