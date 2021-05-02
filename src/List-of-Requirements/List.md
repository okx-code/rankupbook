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
    <td><code>money</code></td>
    <td>number</td>
    <td>no</td>
    <td>yes</td>
    <td>Checks the player's balance and takes the specified amount when ranking up.</td>
    <td><code>money 1000</code></td>
  </tr>
  <tr>
    <td><code>moneyh</code></td>
    <td>number</td>
    <td>no</td>
    <td>no</td>
    <td>Checks the player's balance but does not take the money.</td>
    <td><code>moneyh 10000</code></td>
  </tr>
  <tr>
    <td><code>xp-level</code></td>
    <td>number</td>
    <td>no</td>
    <td>yes</td>
    <td>Checks the player's xp-levels for the specified amount and takes it.</td>
    <td><code>xp-level 30</code></td>
  </tr>
  <tr>
    <td><code>xp-level</code></td>
    <td>number</td>
    <td>no</td>
    <td>no</td>
    <td>Checks the player's xp-levels for the specified amount but does not take them.</td>
    <td><code>xp-level 50</code></td>
  </tr>
  <tr>
    <td><code>playtime-minutes</code></td>
    <td>number</td>
    <td>no</td>
    <td>no</td>
    <td>How long a player has been online, in minutes (uses the Minecraft statistic).</td>
    <td><code>playtime-minutes 120</code></td>
  </tr>
  <tr>
    <td><code>group</code></td>
    <td>text</td>
    <td>no</td>
    <td>no</td>
    <td>Requires a player to be in at least one of a list of groups, separated by spaces.</td>
    <td><code>group vip mvp</code></td>
  </tr>
  <tr>
    <td><code>permission</code></td>
    <td>text</td>
    <td>no</td>
    <td>no</td>
    <td>Requires player to have at least one of a list of permissions, separated by spaces.</td>
    <td><code>permission permission.one permission.two</code></td>
  </tr>
  <tr>
    <td><code>world</code></td>
    <td>text</td>
    <td>no</td>
    <td>no</td>
    <td>Requires a player to be in any of the worlds listed, separated by spaces.</td>
    <td><code>world my_world_nether my_world_the_end</code></td>
  </tr>
  <tr>
    <td><code>player-kills</code></td>
    <td>number</td>
    <td>no</td>
    <td>no</td>
    <td>Players killed. Uses the Minecraft statistic.</td>
    <td><code>player-kills 15</code></td>
  </tr>
  <tr>
    <td><code>total-mob-kills</code></td>
    <td>number</td>
    <td>no</td>
    <td>no</td>
    <td>The total amount of mob kills a player has</td>
    <td><code>total-mob-kills 500</code></td>
  </tr>
  <tr>
    <td><code>mob-kills</code></td>
    <td>number</td>
    <td>yes</td>
    <td>no</td>
    <td><a href="https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/package-summary.html">Mobs</a>
 of the specified type killed. Uses the Minecraft statistic.</td>
    <td><code>mob-kills Skeleton 100</code></td>
  </tr>
  <tr>
    <td><code>item</code></td>
    <td>number</td>
    <td>yes</td>
    <td>yes</td>
    <td>The amount of <a href="https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html">items</a> a player currently has</td>
    <td><code>item DIAMOND 64</code></td>
  </tr>
  <tr>
    <td><code>itemh</code></td>
    <td>number</td>
    <td>yes</td>
    <td>no</td>
    <td>As prior, but does not deduct <a href="https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html">items</a></td>
    <td><code>itemh GLASS 64</code></td>
  </tr>
  <tr>
    <td><code>use-item</code></td>
    <td>number</td>
    <td>yes</td>
    <td>no</td>
    <td>The amount of times a player has used an <a href="https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html">item</a></td>
    <td><code>use-item DIAMOND_SWORD 200</code></td>
  </tr>
  <tr>
    <td><code>block-break</code></td>
    <td>number</td>
    <td>yes</td>
    <td>no</td>
    <td>The amount of times a player has broken a <a href="https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html">block</a></td>
    <td><code>block-break STONE 1000</code></td>
  </tr>
  <tr>
    <td><code>craft-item</code></td>
    <td>number</td>
    <td>yes</td>
    <td>no</td>
    <td>The amount of times a player has crafted an <a href="https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html">item</a></td>
    <td><code>craft-item STONE_BRICKS 256</code></td>
  </tr>
  <tr>
    <td><code>advancement</code></td>
    <td>number</td>
    <td>no</td>
    <td>no</td>
    <td>Checks for a specific Minecraft <a href="https://minecraft.fandom.com/wiki/Advancement#List_of_advancements">advancement</a></td>
    <td><code>advancement story/obtain_armor</code></td>
  </tr>
</table>
