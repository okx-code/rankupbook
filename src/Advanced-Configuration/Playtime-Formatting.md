<title>Playtime Formatting - Official Rankup Wiki</title>
<meta name="description" content="How and why to format the playtime-minutes requirement.">

# Playtime Formatting

When you use the playtime requirement, you might want a different format than Rankup offers. Here you will learn how to do it and get a couple extra tips & tricks on top.

## Default Values & Desired Results
The default output of the unformatted `playtime-minutes` placeholder is `<amount>.0`. The placeholder `{{ rank.req('playtime-minutes').total }}` outputs minutes by default. If you want to change that, you'll need to use math to either divide or multiply the output of the `playtime-minutes` requirement to get your desired result.

Another way to further customize your placeholder with a [filter](../Text-Templating/Formatting.md#filters). We recommend you use the `simple` filter. Keep in mind that the  must be appended at the complete end. Be sure to use the _Filtered Placeholders_ from the table below if you want that.

### Values

| Time Format | Operation | Raw Placeholder                                   | Filtered Placeholder                                            |
| ----------- | --------- | ------------------------------------------------- | --------------------------------------------------------------- |
| Seconds     | `* 60`    | `{{ rank.req('playtime-minutes').total * 60 }}`   | `{{ ( rank.req('playtime-minutes').total * 60 ) \| simple }}`   |
| Hours       | `/ 60`    | `{{ rank.req('playtime-minutes').total / 60 }}`   | `{{ ( rank.req('playtime-minutes').total / 60 ) \| simple }}`   |
| Days        | `/ 1440`  | `{{ rank.req('playtime-minutes').total / 1440 }}` | `{{ ( rank.req('playtime-minutes').total / 1440 ) \| simple }}` |