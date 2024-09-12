# Configuration

## Settings up `settings.json`

Rename `settings Example.json` to `settings.json` and customize your settings.

!!! warning "Note"

    If you are using Genius as your lyrics search engine, you must install the lyricsgenius module `(pip install lyricsgenius)`
    
=== "Latest"

    ```{title="settings.json" .yaml .annotate} 
    {
        "token": "YOUR_BOT_TOKEN", # (1)
        "client_id": "YOUR_BOT_CLIENT_ID", # (2)
        "spotify_client_id": "YOUR_SPOTIFY_CLIENT_ID", # (3)
        "spotify_client_secret": "YOUR_SPOTIFY_CLIENT_SECRET",
        "genius_token": "YOUR_GENIUS_TOKEN", # (4)
        "mongodb_url": "YOUR_MONGODB_URL", # (5)
        "mongodb_name": "YOUR_MONGODB_DB_NAME",
        "nodes": { # (6)
            "DEFAULT": {
                "host": "lavalink",
                "port": 2333,
                "password": "youshallnotpass",
                "secure": false,
                "identifier": "DEFAULT"
            }   
        },
        "prefix": "?", # (7)
        "activity": [ # (8)
            {"type": "listening", "name": "/help", "status": "online"}
        ],
        "logging": { # (9)
            "file": {
                "path": "./logs",
                "enable": true
            },
            "level": {
                "discord": "INFO",
                "vocard": "INFO",
                "ipc_client": "INFO"
            },
            "max-history": 30
        },
        "bot_access_user": [], # (10)
        "embed_color":"0xb3b3b3", # (11)
        "default_max_queue": 1000, # (12)
        "lyrics_platform": "lyrist", # (13)
        "ipc_client": { # (14)
            "host": "127.0.0.1",
            "port": 8000,
            "password": "YOUR_PASSWORD",
            "secure": false,
            "enable": false
        },
        "sources_settings": { # (15)
            "youtube": {
                "emoji": "<:youtube:826661982760992778>",
                "color": "0xFF0000"
            },
            "youtube music": {
                "emoji": "<:youtube:826661982760992778>",
                "color": "0xFF0000"
            },
            "spotify": {
                "emoji": "<:spotify:826661996615172146>",
                "color": "0x1DB954"
            },
            "soundcloud": {
                "emoji": "<:soundcloud:852729280027033632>",
                "color": "0xFF7700"
            },
            "twitch": {
                "emoji": "<:twitch:852729278285086741>",
                "color": "0x9B4AFF"
            },
            "bandcamp": {
                "emoji": "<:bandcamp:864694003811221526>",
                "color": "0x6F98A7"
            },
            "vimeo": {
                "emoji": "<:vimeo:864694001919721473>",
                "color": "0x1ABCEA"
            },
            "apple": {
                "emoji": "<:applemusic:994844332374884413>",
                "color": "0xE298C4"
            },
            "reddit": {
                "emoji": "<:reddit:996007566863773717>",
                "color": "0xFF5700"
            },
            "tiktok": {
                "emoji": "<:tiktok:996007689798811698>",
                "color": "0x74ECE9"
            }
        },
        "default_controller": { # (16)
            "embeds": {
                "active": {
                    "description": "**Now Playing: ```[@@track_name@@]```\nLink: [Click Me](@@track_url@@) | Requester: @@requester@@ | DJ: @@dj@@**",
                    "footer": {
                        "text": "Queue Length: @@queue_length@@ | Duration: @@track_duration@@ | Volume: @@volume@@% {{loop_mode != 'Off' ?? | Repeat: @@loop_mode@@}}"
                    },
                    "image": "@@track_thumbnail@@",
                    "author": {
                        "name": "Music Controller | @@channel_name@@",
                        "icon_url": "@@bot_icon@@"
                    },
                    "color": "@@track_color@@"
                },
                "inactive": {
                    "title": {
                        "name": "There are no songs playing right now"
                    },
                    "description": "[Support](@@server_invite_link@@) | [Invite](@@invite_link@@) | [Questionnaire](https://forms.gle/Qm8vjBfg2kp13YGD7)",
                    "image": "https://i.imgur.com/dIFBwU7.png",
                    "color": "@@default_embed_color@@"
                }
            },
            "default_buttons": [
                ["back", "resume", "skip", {"stop": "red"}, "add"],
                ["tracks"]
            ],
            "disableButtonText": false # (17)
        },
        "default_voice_status_template": "{{@@track_name@@ != 'None' ?? @@track_source_emoji@@ Now Playing: @@track_name@@ // Waiting for song requests}}", # (18)
        "cooldowns": { # (19)
            "connect": [2, 30],
            "playlist view": [1, 30]
        },
        "aliases": { # (20)
            "connect": ["join"],
            "leave": ["stop", "bye"],
            "play": ["p"],
            "view": ["v"]
        }
    }
    ```
    
    1.  Your Discord bot token. You can get it on [Discord Portal](https://discord.com/developers/applications){:target="_blank"}
    2.  **(Optional)** Your Discord bot client ID. You can get it on [Discord Portal](https://discord.com/developers/applications){:target="_blank"}
    3.  Your Spoity client ID and client secret ID. You can get it on [Spotify Portal](https://developer.spotify.com/dashboard/applications){:target="_blank"}
    4.  Your genius api token. You can get it on [Genius Lyrics API](https://genius.com/api-clients){:target="_blank"}
    5.  Your Mongo datebase url and name. You can create MongoDB on [MongoDB](https://www.mongodb.com/){:target="_blank"}
    6.  [Lavalink Server](https://github.com/freyacodes/Lavalink){:target="_blank"} that Vocard will connected! You have to provide host, port, password and identifier of the server.
    7.  You can set the prefix of the bot. If you don't provide any prefix, the bot will disable the message command.
    8.  You can set the activity status of the bot. You can look at some [example here](/2.6.9/config/bot-activity).
    9.  You can configure the logging settings, including the log file path, the logging level for each library, and the maximum history duration for the logs in days.
    10.  By providing the Discord user ID, you can grant these users access to all administrative commands. This will allow them to bypass any limitations imposed on the commands. `Example: [123456789012345678, 876543210987654321, ...]`
    11.  You must pass a [Hexadecimal color](https://htmlcolorcodes.com/){:target="_blank"} code and add `0x` before the color code. `Example: 0xb3b3b3`
    12.  You can set a default maximum number of tracks that can be added to the queue.
    13.  You can set lyrics search engine. `(e.g. A_ZLyrics, Genius, lyrist)`
    14.  You can configure the host, password, and enable the IPC client to connect to your Vocard dashboard.
    15.  You can change the source emoji of the track with discord emoji like `<:EMOJI_NAME:EMOJI_ID>` and change the color of the source in [Hexadecimal color](https://htmlcolorcodes.com/){:target="_blank"}.
    16. You can create your custom embeds and buttons in the player controller. [Example Here](/2.6.9/config/controller/#music-controller)
    17. You can disable the text on the button in the player controller, if you set `true`.
    18. You can set a default voice channel status template while music is playing. Explore available [placeholders](/2.6.9/config/controller/#music-controller) here.
    19. You can set a custom cooldown for the command. `Example: "command_name": [The total number of tokens available, The length of the cooldown period in seconds]`
    20. You can set custom aliases in the command. `Example: "command_name": [alias1, alias2, ...]`

=== "v2.6.8"

    ```{title="settings.json" .yaml .annotate} 
    {
        "nodes": { # (1)
            "DEFAULT": {
                "host": "127.0.0.1",
                "port": 2333,
                "password": "password",
                "secure": false,
                "identifier": "DEFAULT"
            }   
        },
        "prefix": "?", # (2)
        "activity":[
            {"listen": "/help"} # (3)
        ],
        "bot_access_user": [], # (4)
        "embed_color":"0xb3b3b3", # (5)
        "default_max_queue": 1000, # (6)
        "lyrics_platform": "A_ZLyrics", # (7)
        "ipc_server": { # (8)
            "host": "127.0.0.1",
            "port": 8000,
            "enable": false
        },
        "sources_settings": { # (9)
            "youtube": {
                "emoji": "<:youtube:826661982760992778>",
                "color": "0xFF0000"
            },
            "youtube music": {
                "emoji": "<:youtube:826661982760992778>",
                "color": "0xFF0000"
            },
            "spotify": {
                "emoji": "<:spotify:826661996615172146>",
                "color": "0x1DB954"
            },
            "soundcloud": {
                "emoji": "<:soundcloud:852729280027033632>",
                "color": "0xFF7700"
            },
            "twitch": {
                "emoji": "<:twitch:852729278285086741>",
                "color": "0x9B4AFF"
            },
            "bandcamp": {
                "emoji": "<:bandcamp:864694003811221526>",
                "color": "0x6F98A7"
            },
            "vimeo": {
                "emoji": "<:vimeo:864694001919721473>",
                "color": "0x1ABCEA"
            },
            "apple": {
                "emoji": "<:applemusic:994844332374884413>",
                "color": "0xE298C4"
            },
            "reddit": {
                "emoji": "<:reddit:996007566863773717>",
                "color": "0xFF5700"
            },
            "tiktok": {
                "emoji": "<:tiktok:996007689798811698>",
                "color": "0x74ECE9"
            }
        },
        "default_controller": { # (10)
            "embeds": {
                "active": {
                    "description": "**Now Playing: ```[@@track_name@@]```\nLink: [Click Me](@@track_url@@) | Requester: @@requester@@ | DJ: @@dj@@**",
                    "footer": {
                        "text": "Queue Length: @@queue_length@@ | Duration: @@track_duration@@ | Volume: @@volume@@% {{loop_mode != 'Off' ?? | Repeat: @@loop_mode@@}}"
                    },
                    "image": "@@track_thumbnail@@",
                    "author": {
                        "name": "Music Controller | @@channel_name@@",
                        "icon_url": "@@bot_icon@@"
                    },
                    "color": "@@track_color@@"
                },
                "inactive": {
                    "title": {
                        "name": "There are no songs playing right now"
                    },
                    "description": "[Support](@@server_invite_link@@) | [Invite](@@invite_link@@) | [Questionnaire](https://forms.gle/Qm8vjBfg2kp13YGD7)",
                    "image": "https://i.imgur.com/dIFBwU7.png",
                    "color": "@@default_embed_color@@"
                }
            },
            "default_buttons": [
                ["back", "resume", "skip", {"stop": "red"}, "add"],
                ["tracks"]
            ],
            "disableButtonText": false  # (11)
        },
        "cooldowns": { # (12)
            "connect": [2, 30],
            "playlist view": [1, 30]
        },
        "aliases": { # (13)
            "connect": ["join"],
            "leave": ["stop", "bye"],
            "play": ["p"],
            "view": ["v"]
        }
    }
    ```
    
    1.  [Lavalink Server](https://github.com/freyacodes/Lavalink){:target="_blank"} that Vocard will connected! You have to provide host, port, password and identifier of the server.
    2.  You can set the prefix of the bot. If you don't provide any prefix, the bot will disable the message command.
    3.  You can set the activity status of the bot. You can look at some [example here](/2.6.9/config/bot-activity).
    4.  By providing the Discord user ID, you can grant these users access to all administrative commands. This will allow them to bypass any limitations imposed on the commands. `Example: [123456789012345678, 876543210987654321, ...]`
    5.  You must pass a [Hexadecimal color](https://htmlcolorcodes.com/){:target="_blank"} code and add `0x` before the color code. `Example: 0xb3b3b3`
    6.  You can set a default maximum number of tracks that can be added to the queue.
    7.  You can set lyrics search engine. `(e.g. A_ZLyrics, Genius, lyrist)`
    8.  You can set the host, password and enable of the ipc server.
    9.  You can change the source emoji of the track with discord emoji like `<:EMOJI_NAME:EMOJI_ID>` and change the color of the source in [Hexadecimal color](https://htmlcolorcodes.com/){:target="_blank"}.
    10. You can create your custom embeds and buttons in the player controller. [Example Here](/2.6.9/config/controller/#music-controller)
    11. You can disable the text on the button in the player controller, if you set `true`.
    12. You can set a custom cooldown for the command. `Example: "command_name": [The total number of tokens available, The length of the cooldown period in seconds]`
    13. You can set custom aliases in the command. `Example: "command_name": [alias1, alias2, ...]`

=== "v2.6.7"

    ```{title="settings.json" .yaml .annotate } 
    {
        "nodes": { # (1)
            "DEFAULT": {
                "host": "127.0.0.1",
                "port": 2333,
                "password": "password",
                "secure": false,
                "identifier": "DEFAULT"
            }   
        },
        "prefix": "?", # (2)
        "activity":[ # (3)
            {"listen": "/help"}
        ],
        "bot_access_user": [], # (4)
        "embed_color":"0xb3b3b3", # (5)
        "default_max_queue": 1000, # (6)
        "lyrics_platform": "A_ZLyrics", # (7)
        "ipc_server": { # (8)
            "host": "127.0.0.1",
            "port": 8000,
            "enable": false
        },
        "emoji_source_raw": { # (9)
            "youtube": "<:youtube:826661982760992778>",
            "youtube music": "<:youtube:826661982760992778>",
            "spotify": "<:spotify:826661996615172146>",
            "soundcloud": "<:soundcloud:852729280027033632>",
            "twitch": "<:twitch:852729278285086741>",
            "bandcamp": "<:bandcamp:864694003811221526>",
            "vimeo": "<:vimeo:864694001919721473>",
            "apple": "<:applemusic:994844332374884413>",
            "reddit": "<:reddit:996007566863773717>",
            "tiktok": "<:tiktok:996007689798811698>"
        },
        "default_controller": { # (10)
            "embeds": {
                "active": {
                    "description": "**Now Playing: ```[@@track_name@@]```\nLink: [Click Me](@@track_url@@) | Requester: @@requester@@ | DJ: @@dj@@**",
                    "footer": {
                        "text": "Queue Length: @@queue_length@@ | Duration: @@duration@@ | Volume: @@volume@@% {{loop_mode!=Off ?? | Repeat: @@loop_mode@@}}"
                    },
                    "image": "@@track_thumbnail@@",
                    "author": {
                        "name": "Music Controller | @@channel_name@@",
                        "icon_url": "@@bot_icon@@"
                    },
                    "color": "@@default_embed_color@@"
                },
                "inactive": {
                    "title": {
                        "name": "There are no songs playing right now"
                    },
                    "description": "[Support](@@server_invite_link@@) | [Invite](@@invite_link@@) | [Questionnaire](https://forms.gle/Qm8vjBfg2kp13YGD7)",
                    "image": "https://i.imgur.com/dIFBwU7.png",
                    "color": "@@default_embed_color@@"
                }
            },
            "default_buttons": [
                ["back", "resume", "skip", {"stop": "red"}, "add"],
                ["tracks"]
            ]
        },
        "cooldowns": { # (11)
            "connect": [2, 30],
            "playlist view": [1, 30]
        },
        "aliases": { # (12)
            "connect": ["join"],
            "leave": ["stop", "bye"],
            "play": ["p"],
            "view": ["v"]
        }
    }
    ```

    1.  [Lavalink Server](https://github.com/freyacodes/Lavalink){:target="_blank"} that Vocard will connected! You have to provide host, port, password and identifier of the server.
    2.  You can set the prefix of the bot. If you don't provide any prefix, the bot will disable the message command.
    3.  You can set the activity status of the bot. You can look at some [example here](/2.6.9/config/bot-activity).
    4.  By providing the Discord user ID, you can grant these users access to all administrative commands. This will allow them to bypass any limitations imposed on the commands. `Example: [123456789012345678, 876543210987654321, ...]`
    5.  You must pass a [Hexadecimal color](https://htmlcolorcodes.com/){:target="_blank"} code and add `0x` before the color code. `Example: 0xb3b3b3`
    6.  You can set a default maximum number of tracks that can be added to the queue.
    7.  You can set lyrics search engine. `(e.g. A_ZLyrics, Genius)`
    8.  You can set the host, password and enable of the ipc server.
    9.  You can change the source emoji of the track with discord emoji like `<:EMOJI_NAME:EMOJI_ID>`.
    10. You can create your custom embeds and buttons in the player controller. [Example Here](/2.6.9/config/controller/#music-controller)
    11. You can set a custom cooldown for the command. `Example: "command_name": [The total number of tokens available, The length of the cooldown period in seconds]`
    12. You can set custom aliases in the command. `Example: "command_name": [alias1, alias2, ...]`