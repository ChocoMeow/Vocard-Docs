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
=== "Usage"
    ```
    [button_name]
    ```

=== "Usage (Button with color)"
    ```
    [{"button": "color"}]
    ```

| Color Name | Description |
| --- | --- |
| Grey | Color the button grey. |
| Red | Color the button red. |
| Blue | Color the button blue. |
| Green | Color the button green. |

| Button Name | Description |
| --- | --- |
| Back | Skips back to the previous song. |
| Resume | Resume or pause the music. |
| Skip | Skips to the next song. |
| Stop | Disconnects the bot from your voice channel and chears the queue. |
| Loop | Changes Loop mode. `[Off, Track, Queue]` |
| Add | Add the playing track in to your default custom playlist. |
| VolumeUp | Increase player volume by 20%. |
| VolumeDown | Decrease player volume by 20%. |
| VolumeMute | Mute or unmute the player. |
| Autoplay | Enable or disable autoplay mode. |
| Shuffle | Randomizes the tracks in the queue. |
| Forward | Forward 30 seconds in the current track. |
| Rewind | Rewind 30 seconds in the current track. |
| Lyrics | Show the lyrics of the current track in an embedded message. |
| Tracks | If there are tracks in the queue, a drop-down list will be appear. Up to 10 tracks. `(This will take one row)`|
| Effects | Displays all available audio effects that can be applied to the current song. `(This will take one row)` |

=== "Example 1"
    <img width="459" alt="image" src="https://user-images.githubusercontent.com/94597336/221099779-d458e274-6052-4265-afb2-b232de1b1fd4.png">

    ```{title="settings.json" .json}
    "default_buttons": [
        ["back", "resume", "skip", {"stop": "red"}, "add"],
        ["tracks"]
    ]
    ```

=== "Example 2"
    <img width="480" alt="image" src="https://user-images.githubusercontent.com/94597336/221099004-9913ee28-5079-488a-b880-902c7ab7ce38.png">

    ```{title="settings.json" .json}
    "default_buttons": [
        ["back", "resume", "skip", {"stop": "red"}, {"add": "green"}],
        [{"loop": "green"}, {"volumeup": "blue"}, {"volumedown": "blue"}, {"volumemute": "red"}],
        ["tracks"]
    ]
    ```

=== "Example 3"
    <img width="480" alt="image" src="https://user-images.githubusercontent.com/94597336/230248758-14ff7e1b-d6db-49f8-94a6-c55fd02f13df.png">

    ```{title="settings.json" .json}
    "default_buttons": [
        ["autoplay", "shuffle", {"loop": "green"}, "add"],
        ["back", "resume", "skip", {"stop": "red"}],
        ["volumeup", "volumedown", {"mute": "red"}]
    ]
    ```