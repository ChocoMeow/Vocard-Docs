# Bot Activity

## Bot Activity

!!! note
    The activity status will be updated every 10 minutes. If your bot has multiple activities, it will switch to a different activity every 10 minutes.

```{title="Usage" .yaml} 
{
    "type": "@@action@@",
    "name": "@@value@@ some text ...",
    "status": "online"
}
```

| Action Name | Description |
| --- | --- |
| playing | Display the playing status. |
| listening | Display the listening status. |
| watching | Display the watching status. |
| streaming | Display the streaming status. |

| Value Name | Description |
| --- | --- |
| guilds | Number of guilds in the bot. |
| users | Number of users in the voice channel. |
| players | Number of players playing. |
| nodes | Number of nodes are connected. |

| Status | Description |
| --- | --- |
| online | The bot is online. |
| offline | The bot is offline. |
| idle | The bot is idle. |
| dnd | The bot is “Do Not Disturb”. |
| invisible | The bot is “invisible”. |

=== "Example (Single Activity)"
    <img width="200" alt="image" src="https://user-images.githubusercontent.com/94597336/232210610-fb2b8dba-736e-4230-b315-c52b1cf37a22.png">
    ``` {title="settings.json" .json}
    "activity":[
        {"type": "listening", "name": "/help", "status": "online"}
    ]
    ```

=== "Example (Multiple Activity)"
    <img width="200" alt="image" src="https://user-images.githubusercontent.com/94597336/232210610-fb2b8dba-736e-4230-b315-c52b1cf37a22.png">
    <img width="200" alt="image" src="https://user-images.githubusercontent.com/94597336/232210639-255025e2-f55b-422d-a8f8-01cdaeec1e8d.png">
    ```{title="settings.json" .json}
    "activity":[
        {"type": "listening", "name": "/help", "status": "online"}
        {"type": "listening", "name": "@@guilds@@ Guilds", "status": "online"}
        {"type": "watching", "name": "@@players@@ Players", "status": "idle"}
    ]
    ```
