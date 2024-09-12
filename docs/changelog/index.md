# Changelog

Each release typically encompasses a variety of enhancements and corrections. Notable updates, along with any new features and significant alterations, are itemized for your convenience.

## 2.6.9 <small>Sep 02, 2024</small> { id="2.6.9" }

### New Features:
- Added the ability to specify `start` and `end` positions for each song in all play commands. ([33ad427])
- Added voice channel status so others can see what you are playing. ([b0ff4fb])
- Added more customizable placeholders for your music controller and voice channel status. ([b0ff4fb])
- Added a nodes panel to the debug view. ([d4cb50a])
- Added filter selector option in music controller ([bddb9a9])
- Updated bot status for greater customization options. ([72cae9b])
- Implemented a new logging system to enhance our diagnostics. You'll find some new settings related to this in the `settings.json` file. ([4655b6e])
- Rewritten the `IPC Client` code for improved performance and readability. ([f1123b3])
- Rewritten the `swap` and `move` methods in voicelink and added filters to the music controller. ([20bef0e], [9f2e0e5])

### Fixed:
- Resolved an issue that was preventing the 24/7 feature from functioning properly. It's now up and running smoothly. ([9c478c7])
- Removed unnecessary requirements, reducing the project's dependencies and improving build efficiency. ([47389d6])
- Fixed no song suggestions when spotify_client is not given ([33ad427])
- Fixed `zh-tw` localization slash command language pack ([7134287])
- Squashed some bugs to improve the overall performance and stability of our system.

### Breaking Changes:
- Merged `.env` into `settings.json`, consolidating all configuration settings into a single file. ([779ea8b])
- Updated the time representation in the playlist share object from `datetime` to `float`, reducing memory usage and improving performance.
- Updated bot status settings. Check `settings Example.json` for more info. ([72cae9b])

Full Changelog: [v2.6.8a to v2.6.9](https://github.com/ChocoMeow/Vocard/compare/v2.6.8a...v2.6.9)

---

## 2.6.8a <small>July 26, 2024</small> { id="2.6.8a" }

### New Features:
- Added docker configuration for dashboard
- Updated README
- Fixed all instances of typo

Full Changelog: [v2.6.8 to v2.6.8a](https://github.com/ChocoMeow/Vocard/compare/v2.6.8...v2.6.8a)

---

## 2.6.8 <small>February 27, 2024</small> { id="2.6.8" }

### New Features:
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

### Breaking Changes:
- **Collection Name Change**: Please note that the collection name Playlist will be changed to Users. This is a significant change and might affect how you interact with the bot.
- **Sources Settings Update**: More information (color code) has been added into the "sources_settings" field in the settings.json.

Full Changelog: [v2.6.7 to v2.6.8](https://github.com/ChocoMeow/Vocard/compare/v2.6.7...v2.6.8)

---

## 2.6.7 <small>December 15, 2023</small> { id="2.6.7" }

### New Features:
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

---

[9f2e0e5]: https://github.com/ChocoMeow/Vocard/commit/9f2e0e5
[b0ff4fb]: https://github.com/ChocoMeow/Vocard/commit/b0ff4fb
[d4cb50a]: https://github.com/ChocoMeow/Vocard/commit/d4cb50a
[bddb9a9]: https://github.com/ChocoMeow/Vocard/commit/bddb9a9
[72cae9b]: https://github.com/ChocoMeow/Vocard/commit/72cae9b
[4655b6e]: https://github.com/ChocoMeow/Vocard/commit/4655b6e
[f1123b3]: https://github.com/ChocoMeow/Vocard/commit/f1123b3
[20bef0e]: https://github.com/ChocoMeow/Vocard/commit/20bef0e
[9c478c7]: https://github.com/ChocoMeow/Vocard/commit/9c478c7
[47389d6]: https://github.com/ChocoMeow/Vocard/commit/47389d6
[33ad427]: https://github.com/ChocoMeow/Vocard/commit/33ad427
[7134287]: https://github.com/ChocoMeow/Vocard/commit/7134287
[779ea8b]: https://github.com/ChocoMeow/Vocard/commit/779ea8b