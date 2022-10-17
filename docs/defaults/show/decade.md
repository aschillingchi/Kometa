# Decade Collections

The `decade` Metadata File is used to dynamically create collections based on the decades available in your library, sorted by critic rating to create a "best of <decade>"

**This file works with TV Libraries, but has a Movie Library [Counterpart](../movie/decade).**

![](../images/decade.png)

## Collections Section 12

| Collection                                           |                Key                | Description                                                                 |
|:-----------------------------------------------------|:---------------------------------:|:----------------------------------------------------------------------------|
| `Decade Collections`                                 |            `separator`            | [Separator Collection](../separators) to denote the Section of Collections. |
| `Best of <<Decade>>`<br>**Example:** `Best of 2020s` | `<<Year>>`<br>**Example:** `2020` | Collection of Shows released in this Decade.                                |
 
## Config

The below YAML in your config.yml will create the collections:

```yaml
libraries:
  TV Shows:
    metadata_path:
      - pmm: show/decade
```

## Template Variables

Template Variables can be used to manipulate the file in various ways to slightly change how it works without having to make your own local copy.

Note that the `templates_variables:` section only needs to be used if you do want to actually change how the defaults work. Any value not specified is its default value if it has one if not it's just ignored.

All [Shared Collection Variables](../variables) are available as well as the additional Variables below which can be used to customize the file.

| Variable          | Description & Values                                                                                                                                                                                                       |
|:------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `use_separator`   | **Description:** Turn the [Separator Collection](../separators) off.<br>**Values:** `false` to turn of the collection                                                                                                      |
| `sep_style`       | **Description:** Choose the [Separator Style](../separators.md#separator-styles).<br>**Default:** `orig`<br>**Values:** `orig`, `red`, `blue`, `green`, `gray`, `purple`, or `stb`                                         |         
| `limit`           | **Description:** Changes the Builder Limit for all collections in a Defaults file.<br>**Default:** `100`<br>**Values:** Number Greater then 0                                                                              |
| `limit_<<key>>`   | **Description:** Changes the Builder Limit of the specified key's collection.<br>**Default:** `limit`<br>**Values:** Number Greater then 0                                                                                 |
| `sort_by`         | **Description:** Changes the Smart Filter Sort for all collections in a Defaults file.<br>**Default:** `critic_rating.desc`<br>**Values:** [Any `smart_filter` Sort Option](../../metadata/builders/smart.md#sort-options) |
| `sort_by_<<key>>` | **Description:** Changes the Smart Filter Sort of the specified key's collection.<br>**Default:** `sort_by`<br>**Values:** [Any `smart_filter` Sort Option](../../metadata/builders/smart.md#sort-options)                 |
| `exclude`         | **Description:** Exclude these Decades from creating a Dynamic Collection.<br>**Values:** List of Decades found in your library                                                                                            |
| `decade_name`     | **Description:** Changes the title format of the Dynamic Collections.<br>**Default:** `Best of <<key_name>>`<br>**Values:** Any string with `<<key_name>>` in it.                                                          |
| `decade_summary`  | **Description:** Changes the summary format of the Dynamic Collections.<br>**Default:** `Top <<limit>> <<library_translation>>s of the <<key_name>>.`<br>**Values:** Any string.                                           |

The below is an example config.yml extract with some Template Variables added in to change how the file works.

```yaml
libraries:
  TV Shows:
    metadata_path:
      - pmm: decade
        template_variables:
          use_other: false
          use_separator: false
          sep_style: purple
          sort_by: title.asc
```