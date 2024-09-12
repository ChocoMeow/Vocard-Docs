# Languages

Vocard provides support for multiple languages, including both [Localization slash command languages] and standard language packs. Additionally, Vocard allows you to easily customize your own language. Simply follow the steps below.

## Creating a Standard Language Pack

To create a new language pack, follow these steps:

!!! warning "Note"
    Do not alter or remove variables like `{0} {1} ...` as they are essential for the bot's functionality.

1. Go to the `langs` directory and duplicate the `EN.json` file.
2. Rename the copied file with the [desired language code] (e.g., for Korean, use `KO.json`).
3. Open the copied file and replace the existing text with your translations.
4. Once you've made your changes, restart the bot to apply them.

## Creating a Localization Slash Command Language Pack

To create a new localization slash command language pack, follow these steps:

1. Navigate to the `local_langs` directory and duplicate the `zh-TW.json` file.
2. Rename the copied file with the [appropriate language code provided by Discord] (e.g., for Korean, use `ko.json`).
3. Open the copied file and replace the existing text with your translations.
4. Once you've made your changes, [re-sync the bot](#how-to-re-sync-the-bot).

## How to re-sync the bot

1. Stop your bot and open your `settings.json` file.
2. Remove the `version` key inside the settings file.
=== "Before"
    ``` {title="settings.json" .yaml hl_lines="6" .annotate}
    {
        ...
        "play": ["p"],
        "view": ["v"]
    },
    "version": "v2.6.9" # (1)
    ```

    1.  Your version might differ, such as `v2.6.6, v2.6.7, ...` However, this discrepancy is not significant.

=== "After"
    ```{title="settings.json" .json}
    {
        ...
        "play": ["p"],
        "view": ["v"]
    }
    ```
[Localization slash command languages]: https://discord.com/developers/docs/interactions/application-commands#localization
[desired language code]: https://en.wikipedia.org/wiki/List_of_ISO_639_language_codes
[appropriate language code provided by Discord]: https://discord.com/developers/docs/reference#locales
