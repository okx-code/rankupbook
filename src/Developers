Rankup has an API which can be easily hooked in to.
Firstly, to get an instance of the plugin, use
```java
JavaPlugin.getPlugin(sh.okx.rankup.Rankup.class)
```
[Rankups](https://github.com/okx-code/Rankup3/blob/master/src/main/java/sh/okx/rankup/ranks/RankList.java) can be retrieved though `Rankup#getRankups()`

## Events

Rankup provides a `PlayerRankupEvent` and a `PlayerPrestigeEvent` from versions 3.11 onwards.

## Custom requirements

If you would like to register your own requirements through Rankup, listen to the event [`sh.okx.rankup.events.RankupRegisterEvent`](https://github.com/okx-code/Rankup3/blob/master/src/main/java/sh/okx/rankup/events/RankupRegisterEvent.java).

When it is called, you can use `RankupRegisterEvent#addRequirement` to register requirements.

Please note that this event can be called multiple times, such as when `/pru reload` is run. 

### Creating requirements

Rankup employs the prototype pattern for requirements. One instance is created, and it is cloned for each rank that has said requirement. Therefore, you must provide functionality for this.

Here is a simple example requirement for a player to be in a certain gamemode:

```java
public class GamemodeRequirement extends Requirement {
  public GamemodeRequirement(Rankup plugin) {
    super(plugin, "gamemode");
  }

  private GamemodeRequirement(Requirement clone) {
    super(clone);
  }

  @Override
  public boolean check(Player player) {
    return player.getGameMode().name().equalsIgnoreCase(getValueString());
  }

  @Override
  public Requirement clone() {
    return new GamemodeRequirement(this);
  }
}
```

If your requirement is not a true or false value and is instead a progessive number (eg money) you can extend [`sh.okx.rankup.requirements.ProgessiveRequirement`](https://github.com/okx-code/Rankup3/blob/master/src/main/java/sh/okx/rankup/requirements/ProgressiveRequirement.java) and the method `double Requirement#getProgess(Player)`. From there you can just return the number (ie a player's money).

If you would like to do something once a player ranks up with a rank using your requirement, you may also implement  [`sh.okx.rankup.requirements.DeductibleRequirement`](https://github.com/okx-code/Rankup3/blob/master/src/main/java/sh/okx/rankup/requirements/DeductibleRequirement.java). 

If you need any help, please, contact me on [Rankup's Discord server](https://discord.gg/H4Wqu4D).
