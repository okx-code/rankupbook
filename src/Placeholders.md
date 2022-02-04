<html>
  <head>
    <meta name="description" content="Reference for all Placeholders provided by Rankup3 and their usage.">
    <meta name="keywords" content="Rankup, Minecraft, Plugin, Spigot, Prestige">
  </head>
  <style>
    code { white-space: nowrap !important; } /* protect code from wrapping to make selecting and copying easier. */
  </style>
</html>

# Kinds of Placeholders
> There are 2 kinds of supported placeholders:
> - [Pebble](./Text-Templating.html) (preferred)  
> - [PAPI](./Spigot/PAPI.html) (external/soft-dependent)  
> `Old Placeholders` are deprecated and may be removed in later versions.  

## PAPI Placeholders
> Both Pebble and PAPI Placeholders are included with Rankup. `No ecloud download required`.  
> PlaceholderAPI placeholders can be used anywhere a `Placeholder` can be used inside Rankup's messages.  
> However, PAPI Placeholders are intended for use in **other plugins**.  
> Only use PAPI Placeholders from the Rankup Expansion inside of rankup's files when working inside a **non-rankup PAPI placeholder**.  
> To use Rankup's PAPI placeholders in MVdW Placeholder plugins like FeatherBoard, use `{placeholderapi_<PAPI>}` instead of `%PAPI%`.  
> For example, you might use `{placeholderapi_rankup_current_rank}` instead of `%rankup_current_rank%` in FeatherBoard.  

## Sub-requirements in placeholders
> Requirements that support sub-requirements use the format <code>\<requirement> \<sub-requirement> \<amount></code>.  
> In placeholders, sub-requirements are <code>rank.req('\<requirement\>#\<sub-requirement\>')</code> or <code>rank.req('\<requirement\>', '\<sub-requirement\>')</code>.  
> For example, with **[Pebble Placeholders](#placeholders)** can use either:  
> - `{{ rank.requirement('block-break', 'STONE').total }}`  
> - `{{ rank.requirement('block-break#STONE').total }}`  
> Or in [PlaceholderAPI](./Spigot/PAPI.html):  
> - `%rankup_requirement_block-break#STONE%`  
> Use the spigot enum pages for [mobs](./Spigot/Docs/mobs.html) and [items](./Spigot/Docs/materials.html) when declared in requirements.  

# Placeholders
> **NOTE:** When a `Placeholder` outputs an unwanted decimal, like `{{ rank.requirement('xp-level').total }}` printing `5.0`, use a [filter to control the decimals](./Text-Templating/Formatting.html#filters).

Pebble Placeholder | Rankup PAPI Expansion | Old Placeholder | Retrieved From | Description
- | - | - | - | -
<code>{{ player }}</code> | N/A | `{PLAYER}` | N/A | The calling player's name.
<code>{{ rank }}</code> | <code>%rankup\_current\_rank%</code> | `{OLD_RANK}` | [`rank:`](../Rankups-and-Prestiges/How-to-Rankups.yml.md#2-rank) | Player's current rank.
<code>{{ rank.name }}</code> | <code>%rankup\_current\_rank\_name%</code> | `{OLD_RANK_NAME}` | [`display-name:`](../Rankups-and-Prestiges/Optionals.md#2-display-name) | `display-name:` of the current rank.
<code>{{ next }}</code> | <code>%rankup\_next\_rank%</code> | `{RANK}` | [`next:`](../Rankups-and-Prestiges/How-to-Rankups.yml.md#3-next) | Player's next rank.
<code>{{ next.name }}</code> | <code>%rankup\_next\_rank\_name%</code> | `{RANK_NAME}` | [`display-name:`](../Rankups-and-Prestiges/Optionals.md#2-display-name) | `display-name:` of the next rank.
<code>{{ rank.from }}</code> | <code>%rankup\_current\_prestige%</code> | `{FROM}` | [`from:`](../Rankups-and-Prestiges/How-to-Prestiges.yml.md#on-from-and-to) | Player's current prestige.
<code>{{ rank.to }}</code> | <code>%rankup\_next\_prestige%</code> | `{TO}` | [`to:`](../Rankups-and-Prestiges/How-to-Prestiges.yml.md#on-from-and-to) | Player's next prestige.
None Equivalent | <code>%rankup\_status\_\<rank\>%</code> | None Equivalent | [`status:`](./GitHub/Rankup3/config/Status.html) | Player's completion [`status:`](./GitHub/Rankup3/config/Status.html) for the `<rank>`.
<code>{{ seconds.remaining }}</code> | None Equivalent | `{SECONDS_LEFT}` | [`cooldown:`](../GitHub/Rankup3/config/Cooldown.html) | Seconds left on a command cooldown.
<code>{{ seconds }}</code> | None Equivalent | `{SECONDS}` | [`cooldown:`](../GitHub/Rankup3/config/Cooldown.html) | Total command cooldown time in a rankup or prestige.
  <!-- None Equivalent | <code>%rankup\_current\_prestige\_name%</code> | None Equivalent | [`display-name`](../Rankups-and-Prestiges/Optionals.md#2-display-name) | `display-name` of the player's current prestige. -->
  <!-- None Equivalent | <code>%rankup\_next\_prestige\_name%</code> | None Equivalent | [`display-name`](../Rankups-and-Prestiges/Optionals.md#2-display-name) | `display-name` of the next prestige. -->
## Requirement Placeholders
> Use a requirement from the [List of Requirements](./List-of-Requirements.md#list) in place of `<requirement>` throughout the examples.

Pebble Placeholder | Rankup PAPI Expansion | Old Placeholder | Description
- | - | - | -
<code>{{ rank.req('\<requirement\>').total }}</code> | <code>%rankup\_requirement\_\<requirement\>%</code> | `{AMOUNT <requirement>}` | Total `<requirement>`.
<code>{{ rank.req('\<requirement\>').progress }}</code> | <code>%rankup\_requirement\_\<requirement\>\_done%</code> | `{AMOUNT_DONE <requirement>}` | Progress towards `<requirement>`.
<code>{{ rank.req('\<requirement\>').remaining }}</code> | <code>%rankup\_requirement\_\<requirement\>\_left%</code> | `{AMOUNT_NEEDED <requirement>}` | Remaining `<requirement>`.
<code>{{ rank.req('\<requirement\>').percent \| percent }}</code> | <code>%rankup\_requirement\_\<requirement\>\_percent\_done%</code> | `{PERCENT_DONE <requirement>}` | Progress towards `<requirement>` in percent.
<code>{{ (100 - rank.req('\<requirement\>').percent) \| percent }}</code> | <code>%rankup\_requirement\_\<requirement\>\_percent\_left%</code> | `{PERCENT_LEFT <requirement>}` | Remaining `<requirement>` in percent.
  <!-- <code>{{ ranks\[\<rank\>\].req('\<requirement\>').total }} </code> | <code>%rankup\_rank\_requirement\_\<rank\>\_\<requirement\>%</code> | None Equivalent | Total Amount of `<requirement>` for `<rank>`. -->
  <!-- <code>{{ ranks\[\<rank\>\].req('\<requirement\>').percent \| percent }} </code> | <code>%rankup\_rank\_requirement\_\<rank\>\_\<requirement\>\_percent\_done%</code> | None Equivalent | Amount done of `<requirement>` for `<rank>` in percent. -->
  <!-- <code>{{ (100 - ranks\[\<rank\>\].req('\<requirement\>').percent) \| percent }}</code> | <code>%rankup\_rank\_requirement\_\<rank\>\_\<requirement\>\_percent\_left%</code> | None Equivalent | Progress as a percentage of `<requirement>` for `<rank>` in percent. -->
## Rankup PAPI Expansion Money Requirement Placeholders
> The following money requirement placeholders provided by the Rankup PAPI Expansion only use the first of one of `money` or `moneyh` when both are listed in the `requirements:` section of a rankup or prestige step.  

Rankup PAPI Expansion | Description
- | -
<code>%rankup\_money%</code> OR <code>%rankup\_prestige\_money%</code> | Total amount required to rankup or prestige.
<code>%rankup\_money\_formatted%</code> OR <code>%rankup\_prestige\_money\_formatted%</code> | As above, formatted by [`shorten:`](./GitHub/Rankup3/config/Shorten.html).
<code>%rankup\_money\_left%</code> OR <code>%rankup\_prestige\_money\_left%</code> | Remaining amount required before the player may rankup or prestige.
<code>%rankup\_money\_left\_formatted%</code> | As above, formatted with the [money filter](./Text-Templating/Formatting.html#filters).
<code>%rankup\_percent\_done%</code> | Progress as a percent of the total of the money requirement.
<code>%rankup\_percent\_done\_formatted%</code> | As above, formatted to 2 decimals.
<code>%rankup\_percent\_left%</code> | Remaining required as a percent of the total of the money requirement.
<code>%rankup\_percent\_left\_formatted%</code> | As above, formatted to 2 decimals.
## Money Placeholders
> To facilitate transitioning to the new Pebble Templates, corresponding `Pebble Placeholder` alternatives to each `Old Placeholder` for money are listed below.  

Pebble Placeholder | Old Placeholder | Description
- | - | - 
<code>{{ rank.req('money').total }}</code> | `{AMOUNT money}` | Total `money`.
<code>{{ rank.req('moneyh').total }}</code> | `{AMOUNT moneyh}` | Total `moneyh`.
<code>{{ rank.req('money').total \| money }}</code> | `{MONEY}` | Total `money` formatted using the [money filter](./Text-Templating/Formatting.html#filters).
<code>{{ rank.req('moneyh').total \| money }}</code> | `{MONEY}` | Total `moneyh` formatted using the [money filter](./Text-Templating/Formatting.html#filters).
<code>{{ rank.req('money').remaining }}</code> | `{AMOUNT_NEEDED money}` | Remaining `money`.
<code>{{ rank.req('moneyh').remaining }}</code> | `{AMOUNT_NEEDED moneyh}` | Remaining `moneyh`.
<code>{{ rank.req('money').remaining \| money }}</code> | `{MONEY_NEEDED}` | Remaining `money` formatted using the [money filter](./Text-Templating/Formatting.html#filters).
<code>{{ rank.req('moneyh').remaining \| money }}</code> | `{MONEY_NEEDED}` | Remaining `moneyh` formatted using the [money filter](./Text-Templating/Formatting.html#filters).
<code>{{ rank.req('money').percent \| percent }}</code> | `{PERCENT_DONE money}` | Progress towards `money` in percent.
<code>{{ rank.req('moneyh').percent \| percent }}</code> | `{PERCENT_DONE moneyh}` | Progress towards `moneyh` in percent.
<code>{{ (100 - rank.req('money').percent) \| percent }}</code> | `{PERCENT_LEFT money}` | Remaining `money` in percent.
<code>{{ (100 - rank.req('moneyh').percent) \| percent }}</code> | `{PERCENT_LEFT moneyh}` | Remaining `moneyh` in percent.
  <!-- <code>%rankup\_rank\_money\_\<rank\>%</code> -->
  <!-- <code>%rankup\_rank\_money\_\<rank\>\_left%</code> -->
