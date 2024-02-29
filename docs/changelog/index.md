# Changelog

Each release typically encompasses a variety of enhancements and corrections. Notable updates, along with any new features and significant alterations, are itemized for your convenience.

## Vocard Bot

### 2.6.8 <small>February 27, 2024</small> { id="2.6.8" }

- **Updated Language Packs**: We've refreshed the UA (Ukrainian) and RU (Russian) language packs.
- **Rewritten Placeholder Code**: We've introduced new placeholders, `track_author` and `track_color`, for more customization.
- **Dockerfile and Docker-compose**: We've simplified installation with Docker and included MongoDB in the docker-compose setup.
- **Improved Database Performance**: We've switched to `motor` for faster MongoDB interactions.
- **Command Changes**: We've removed the `chapters command` and added `autocomplete` in the play command, which now searches with the `Spotify API` for more efficient and accurate searches.
- **Disable Button Text Option**: We've added a disable button text option in `settings.json`, allowing you to customize the disable controller button text as per your preference.
- **Embed View Change**: We've changed the embed view in the `/playlist view` command for a better user experience.
- **More Typehints**: We've added more typehints into the code to make it more understandable and easier to work with.
- **Python 3.12 Support**: Vocard now supports `Python 3.12`.
- **Track URLs**: We've added track URLs and redesigned the queue, history, and playlist command views.
- **Played History Feature**: We've added a new played history feature to keep track of your tunes.
- **Code Optimizations**: We've made several code optimizations to improve the bot's performance.
- **Fixed MP3 URLs**: You can now play songs with `custom MP3 URLs`.
- **New Lyrics Search Platform**: We've added a new search lyrics platform, `Lyrist`, and rewritten the lyrics command. You can now enter the `song title` and the `song author` for better searching.
- **Rewritten Placeholder Expression Features**: Placeholder expressions have been rewritten for faster execution and more comprehensive actions in the player controller.

#### Breaking Changes:
- **Collection Name Change**: Please note that the collection name Playlist will be changed to Users. This is a significant change and might affect how you interact with the bot.
- **Sources Settings Update**: More information (color code) has been added into the "sources_settings" field in the settings.json.

Full Changelog: [v2.6.7 to v2.6.8](https://github.com/ChocoMeow/Vocard/compare/v2.6.7...v2.6.8)

### 2.6.7 <small>December 15, 2023</small> { id="2.6.7" }

- Only supported for `Lavalink v4.0.0` or above
- Added thumbnail in nowplaying embed
- Added UA language pack
- Added helpful guide embed when your command was missing arguments
- Dump discord.py package update (2.3.1 -> 2.3.2)
- Fixed seek function in dashboard
- Fixed playlist playback fix
- Code clean-up and performance improvement
- Rewrite debugging command

Full Changelog: [v2.6.6 to v2.6.7](https://github.com/ChocoMeow/Vocard/compare/v2.6.6...v2.6.7)