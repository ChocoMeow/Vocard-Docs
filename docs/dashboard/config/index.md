# Configuration

## Settings up `settings.json`

Rename `settings Example.json` to `settings.json` and customize your settings.

=== "Latest"

    ```{title="settings.json" .yaml .annotate} 
    {
        "host": "localhost", # (1)
        "port": "8080", # (2)
        "password": "", # (3)
        "client_id": "", # (4)
        "client_secret_id": "", # (5)
        "secret_key": "", # (6)
        "redirect_url": "http://127.0.0.1:8080/callback", # (7)
        "logging": { # (8)
            "file": {
                "path": "./logs", # (9)
                "enable": true # (10)
            },
            "level": {
                "dashboard": "INFO" # (11)
            },
            "max_history": 30 # (12)
        }
    }
    ```
    
    1.  The hostname or IP address where the webapp will run. 'localhost' means it's accessible only from the same machine.
    2.  The port number on which the webapp will listen for incoming requests. Default is often 8080
    3.  The password required for the vocard bot to connect to the dashboard. This should be kept secure and not shared publicly.
    4. The client ID for the Discord bot used for OAuth authentication with Discord users. Required for user login and authorization. Get this from the Discord Developer Portal.
    5. The client secret associated with the Discord bot's client ID. This is used to securely authenticate the bot during the OAuth process. Obtain this from the Discord Developer Portal.
    6. A secret key used by webapp for secure sessions and CSRF protection. It is important to keep this value secret.
    7. The URL to which users will be redirected after authentication. Typically points to a callback endpoint in your app.
    8. Configuration for logging within the application.
    9. The directory where log files will be stored. Ensure this path exists and is writable.
    10. A flag to enable or disable logging to files. Set to true to log messages to the specified path.
    11. The logging level for the dashboard component of your app. 'INFO' captures general operational messages.
    12. The maximum number of log entries to keep in history, useful for limiting log size.

## Adding Redirect URL
1. Open your browser and go to the [Discord Developer Portal].
2. Select your application.
3. Navigate to the OAuth2 section.
4. Click Add Redirect and paste the redirect_url you set in settings.json.

[Discord Developer Portal]: https://discord.com/developers/applications