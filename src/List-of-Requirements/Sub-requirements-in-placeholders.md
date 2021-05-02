# How to specify sub-requirements in placeholders

Requirements that support sub-requirements are used in the format `<requirement> <sub-requirement> <amount>`. In placeholders, sub-requirements are `<requirement>#<sub-requirement>`.

For example, you might have `requirements-not-met: 'You have {AMOUNT_DONE block-break#STONE}/{AMOUNT block-break#stone}. {AMOUNT_NEEDED block-break#STONE} stone left to break.'`, or in PlaceholderAPI, `%rankup_requirement_block-break#stone%`
Use the spigot enum pages for [entities](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/package-summary.html) and [items](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/material/package-summary.html) when declared in requirements.
