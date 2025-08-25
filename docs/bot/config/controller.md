# Controller

You can create a custom embed and button for the Music Controller in Vocard for each guild. This Music Controller displays the current playback status, including details like whether a track is looping and the number of songs in the queue. Additionally, the controller buttons allow you to perform actions such as pause, skip, forward, rewind, and go back, eliminating the need to type commands.

## Music Controller

### Embeds
=== "Usage Of Placeholder"
    ```
    @@value@@
    ```

=== "Usage Of Expression"
    ```
    {{ EXPRESSION ?? TRUE // FALSE }}
    ```

| Value Name | Description |
| --- | --- |
| channel_name | The name of the channel the bot is playing on. |
| track_name | The name of the track currently playing. |
| track_url | The url of the track currently playing. |
| track_author | The name of the author of the track currently playing. |
| track_duration | The length of the track currently playing. |
| track_thumbnail | The thumbnail of the track currently playing. |
| track_color | The color associated with the source for the currently playing track. For example, YouTube tracks are indicated in red. This color can be customized in the settings.json file |
| track_requester_id | The id of the requester for the currently playing track. |
| track_requester_name | The name of the requester for the currently playing track. |
| track_requester_mention | The mention of the requester for the currently playing track. |
| track_requester_avatar | The avatar url of the requester for the currently playing track. |
| track_source_name | The name of the source for the currently playing track. |
| track_source_emoji | The emoji of the source for the currently playing track. |
| queue_length | Number of queue lengths |
| volume | Music volume. |
| dj | DJ role. `(It can be a user or role)` |
| loop_mode | Current repeat mode. |
| default_embed_color | Default embed color. `(color_code in settings.json)` |
| bot_icon | The avatar of the bot. |
| server_invite_link | The invite url of the support server |
| invite_link | The invite url of the bot. |
| t_<name_of_the_translation> | The translation of the text based on your server settings. For example, t_buttonBack will display as 返回 if your language setting is set to Chinese. |

=== "Example 1"
    <div class="grid" markdown>
        <img width="450" alt="image" src="https://user-images.githubusercontent.com/94597336/232209745-e55de4e5-e4f2-47ce-ab78-69e9263f321a.png">
        <img width="450" alt="image" src="https://user-images.githubusercontent.com/94597336/232209778-e30f2f92-a179-4eb6-90d9-865cb1903699.png">
    </div>
    ```{title="settings.json" .json}
    "default_controller": {
        "embeds": {
            "active": {
                "description": "**Now Playing: ```[@@track_name@@]```\nLink: [Click Me](@@track_url@@) | Requester: @@track_requester_mention@@ | DJ: @@dj@@**",
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
        }
    },
    ```


### Buttons
This documentation provides a detailed breakdown of the custom button configuration in our application.

#### Button Styles
Each style serves a different purpose and can be used to convey the button's function more effectively. For more details on button styles, refer to the [Discord ButtonStyle Documentation](https://discordpy.readthedocs.io/en/stable/interactions/api.html?highlight=button%20style#discord.ButtonStyle)

| Style Name | Description |
| --------------------------- | --- |
| Grey | A neutral color that blends well with most themes, ideal for secondary actions. |
| Red | A bold color that signifies danger or stop actions, used for critical functions like stopping or disconnecting. |
| Blurple | A vibrant blue hue that attracts attention, suitable for primary actions like play or start. |
| Green | Represents success or positive actions. |

#### Button Types
We categorize buttons into three types for easier understanding: `normal buttons`, `state-based buttons`, and `full-width select buttons`.

1. Normal Buttons
    
    Normal buttons are simple and can include an emoji, label, and optional style. Here are the details:

    | Button Name | Description |
    | --- | --- |
    | Back | Skips back to the previous song. |
    | Skip | Skips to the next song. |
    | Stop | Disconnects the bot from your voice channel and chears the queue. |
    | Forward | Forward 30 seconds in the current track. | |
    | VolumeUp | Increase player volume by 20%. |
    | VolumeDown | Decrease player volume by 20%. |
    | Autoplay | Enable or disable autoplay mode. |
    | Shuffle | Randomizes the tracks in the queue. |
    | Rewind | Rewind 30 seconds in the current track. |
    | Lyrics | Show the lyrics of the current track in an embedded message. |

    === "Back"
        ```{title="settings.json" .json}
        "buttons": [
            {
                "back": {
                    "emoji": "⏮️",
                    "label": "@@t_buttonBack@@",
                    "style": "grey"
                }
            }
        ]
        ```
    
    === "Stop"
        ```{title="settings.json" .json}
        "buttons": [
            {
                "stop": {
                    "emoji": "⏹️",
                    "label": "@@t_buttonLeave@@",
                    "style": "red"
                }
            }
        ]
        ```

2. States Based Button
    
    These buttons change based on their current state, allowing for different actions. A key example is the play-pause button.

    | Button Name | Description | States |
    | --- | --- | --- |
    | Play-Pause | Resume or pause the music. | pause, resume |
    | Loop | Changes Loop mode. `[Off, Track, Queue]` | off, track, queue |
    | VolumeMute | Mute or unmute the player. | mute, muted |

    === "Play-Pause"
        ```{title="settings.json" .json}
        "buttons": [
            {
                "play-pause": {
                    "states": {
                        "pause": {
                            "emoji": "⏸️",
                            "label": "@@t_buttonPause@@",
                            "style": "red"
                        },
                        "resume": {
                            "emoji": "▶️",
                            "label": "@@t_buttonResume@@",
                            "style": "green"
                        }
                    }
                }
            }
        ]
        ```

    === "Loop"
        ```{title="settings.json" .json}
        "buttons": [
            {
                "loop": {
                    "states": {
                        "off": {
                            "emoji": "🚫",
                            "label": "Off",
                            "style": "grey"
                        },
                        "track": {
                            "emoji": "🔁",
                            "label": "Track",
                            "style": "green"
                        },
                        "queue": {
                            "emoji": "🔂",
                            "label": "Queue",
                            "style": "blurple"
                        }
                    }
                }
            }
        ]
        ```

3. Full-Width Select Buttons
    
    These buttons span the entire width of the row and are typically used for selecting options, like tracks or effects.

    | Button Name | Description | Additional Options |
    | --- | --- | --- |
    | Tracks | If there are tracks in the queue, a drop-down list will be appear. Up to 25 tracks. | max_options (int) |
    | Effects | Displays all available audio effects that can be applied to the current song. |

    === "Tracks"
        ```{title="settings.json" .json}
        "buttons": [
            {
                "tracks": {
                    "label": "@@t_buttonBack@@",
                    "max_options": 25
                }
            }
        ]
        ```
    
    === "Effects"
        ```{title="settings.json" .json}
        "buttons": [
            {
                "effects": {
                    "label": "@@t_buttonLeave@@"
                }
            }
        ]
        ```

#### Button Example

=== "Example 1"
    <img width="459" alt="image" src="https://user-images.githubusercontent.com/94597336/221099779-d458e274-6052-4265-afb2-b232de1b1fd4.png">

    ```{title="settings.json" .json}
    "buttons": [
        {
            "back": {
                "emoji": "⏮️",
                "label": "@@t_buttonBack@@"
            },
            "play-pause": {
                "states": {
                    "pause": {
                        "emoji": "⏸️",
                        "label": "@@t_buttonPause@@"
                    },
                    "resume": {
                        "emoji": "▶️",
                        "label": "@@t_buttonResume@@"
                    }
                }
            },
            "skip": {
                "emoji": "⏭️",
                "label": "@@t_buttonSkip@@"
            },
            "stop": {
                "emoji": "⏹️",
                "label": "@@t_buttonLeave@@",
                "style": "red"
            },
            "add-fav": {
                "emoji": "❤️",
                "label": ""
            }
        },
        {
            "tracks": {
                "label": "@@t_playerDropdown@@",
                "max_options": 10
            }
        }
    ]
    ```

=== "Example 2"
    <img width="480" alt="image" src="https://user-images.githubusercontent.com/94597336/221099004-9913ee28-5079-488a-b880-902c7ab7ce38.png">

    ```{title="settings.json" .json}
    "buttons": [
        {
            "back": {
                "emoji": "⏮️",
                "label": "@@t_buttonBack@@"
            },
            "play-pause": {
                "states": {
                    "pause": {
                        "emoji": "⏸️",
                        "label": "@@t_buttonPause@@"
                    },
                    "resume": {
                        "emoji": "▶️",
                        "label": "@@t_buttonResume@@"
                    }
                }
            },
            "skip": {
                "emoji": "⏭️",
                "label": "@@t_buttonSkip@@"
            },
            "stop": {
                "emoji": "⏹️",
                "label": "@@t_buttonLeave@@",
                "style": "red"
            },
            "add-fav": {
                "emoji": "❤️",
                "label": "green"
            }
        },
        {
            "loop": {
                "states": {
                    "off": {
                        "emoji": "🚫",
                        "label": "Loop"
                    },
                    "track": {
                        "emoji": "🔁",
                        "label": "Loop",
                        "style": "green"
                    },
                    "queue": {
                        "emoji": "🔂",
                        "label": "Loop"
                    }
                }
            },
            "volumeup": {
                "emoji": "🔊",
                "label": "@@t_buttonVolumeUp@@",
                "style": "blurple"
            },
            "volumedown": {
                "emoji": "🔉",
                "label": "@@t_buttonVolumeDown@@",
                "style": "blurple"
            },
            "volumemute": {
                "states": {
                    "muted": {
                        "emoji": "🔈",
                        "label": "@@t_buttonVolumeUnmute@@"
                    },
                    "mute": {
                        "emoji": "🔇",
                        "label": "@@t_buttonVolumeMute@@",
                        "style": "red"
                    }
                }
            }
        }
        {
            "tracks": {
                "label": "@@t_playerDropdown@@",
                "max_options": 10
            }
        }
    ]
    ```