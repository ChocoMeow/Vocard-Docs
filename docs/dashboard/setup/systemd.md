# Systemd Service

If you're running a Systemd-based Linux distribution, you may want to run Vocard Dashboard as a background service. To set this up, create a `vocard-dashboard.service` file in the `/usr/lib/systemd/system` directory. Use the template below, ensuring you replace the placeholders within the `<>` brackets with your specific values:

```ini title="vocard-dashboard.service"
[Unit]
# Description of the service
Description=Vocard Dashboard Service

# Ensure the service starts after logging and networking are available
After=syslog.target network.target

[Service]
# User and group under which the bot will run
User=<usr>
Group=<usr>

# Directory where the application is located
WorkingDirectory=</home/usr/vocard-dashboard>

# Command to install dependencies and start the bot
ExecStart=/bin/bash -c 'pip install --no-cache-dir -r requirements.txt && python3 main.py'

# Restart the service if it fails
Restart=on-failure

# Wait 5 seconds before restarting
RestartSec=5s

[Install]
# Enable the service to start on boot
WantedBy=multi-user.target
```

To initiate the Vocard Dashboard service, execute the following command

```
$ sudo systemctl daemon-reload
$ sudo systemctl enable vocard-dashboard
$ sudo systemctl start vocard-dashboard
```

In addition to the standard log files, you can view the service logs using:
```
$ sudo journalctl -u vocard-dashboard
```