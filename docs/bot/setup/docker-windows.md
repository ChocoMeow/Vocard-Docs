# Docker Setup Guide for Windows

This guide explains how to set up Vocard using Docker Desktop on a Windows system. Follow the steps carefully to ensure a successful installation.

## Prerequisites

-   **Docker Desktop**: Download and install it from the [official Docker Desktop for Windows guide](https://docs.docker.com/desktop/install/windows-install/). This includes Docker Engine and Docker Compose.

!!! note

    After installation, ensure Docker Desktop is running. You can verify Docker is working by opening PowerShell and running:
    ```powershell
    docker --version
    docker compose version
    ```
    If either command fails, ensure Docker Desktop is installed and running.

## Installation Options

Choose one of the following methods to install Vocard. **Method 1 (Pre-built Images)** is recommended for most users due to its simplicity.

### Method 1: Using Pre-built Images <small>recommended</small>

This method uses pre-built Docker images for a quick and straightforward setup.

1.  **Open PowerShell as Administrator**

    Right-click the Start menu, select **Windows PowerShell (Admin)**, and confirm any UAC prompts.

2.  **Create Project Directory**

    Create a directory for your Vocard project and navigate to it:

    ```powershell
    New-Item -Path "C:\Program Files\vocard\lavalink" -ItemType Directory -Force
    Set-Location -Path "C:\Program Files\vocard\"
    ```

3.  **Download Config Files**

    !!! warning

        Existing files in the directory will be overwritten. Back up any existing configurations if needed.

    ```powershell
    Invoke-WebRequest -Uri "https://raw.githubusercontent.com/ChocoMeow/Vocard/refs/heads/main/settings%20Example.json" -OutFile "settings.json"
    Invoke-WebRequest -Uri "https://raw.githubusercontent.com/ChocoMeow/Vocard/refs/heads/main/examples/application.yml" -OutFile "lavalink\application.yml"
    Invoke-WebRequest -Uri "https://raw.githubusercontent.com/ChocoMeow/Vocard/refs/heads/main/lavalink/Dockerfile-lavalink" -OutFile "lavalink\Dockerfile-lavalink"
    Invoke-WebRequest -Uri "https://raw.githubusercontent.com/ChocoMeow/Vocard/refs/heads/main/docker-compose.yml" -OutFile "docker-compose.yml"
    ```

4.  **Modify Configurations**

    !!! note

        Consider using a code editor like [Visual Studio Code](https://code.visualstudio.com/download) for easier JSON and YAML editing.
        Refer to the Guide to Bot Configuration for details on required values (e.g., MongoDB URL, Lavalink password).

    ```powershell
    notepad settings.json
    notepad lavalink\application.yml
    ```

    Edit files with your credentials/values according to this [Bot Configuration Guide].

5.  **Verify Configuration**

    - Ensure ports in `docker-compose.yml` match those in `settings.json` and `application.yml`. Defaults are:
        - Lavalink: `2333`
        - MongoDB: `27017`
    - Vocard uses a local Docker network, so ports are not exposed publicly unless modified.
    - Verify all mandatory tokens are set in `settings.json`.

6.  **Start Containers** (Launch the containers in detached mode)

    ```powershell
    docker compose up -d
    ```

### Method 2: Build from Source

This method builds Vocard from the source code, offering more control over the setup.

!!! note

    Ensure [Git](https://git-scm.com) for Windows is installed to use the git command.

1. **Clone Repository** (Clone the Vocard repository and navigate to it)
    ```powershell
    git clone https://github.com/ChocoMeow/Vocard.git C:\Program Files\vocard
    Set-Location -Path "C:\Program Files\vocard"
    ```

2. **Enable Builds in docker-compose.yml**

    Open docker-compose.yml in your editor and for each service:

    
    - Edit `docker-compose.yml` to enable building from source:
        - For both `vocard` and `lavalink` services:
            - Uncomment the `build` sections.
            - Comment out the `image` lines.

    Example for the vocard service:


    ```yaml
    vocard:
    # image: ghcr.io/chocomeow/vocard:latest
    build:
        context: .
        dockerfile: ./Dockerfile
    ```

3. **Prepare Config Files**

    !!! note

        Consider using a code editor like [Visual Studio Code](https://code.visualstudio.com/download) for easier JSON and YAML editing.
        Refer to the Guide to Bot Configuration for details on required values (e.g., MongoDB URL, Lavalink password).

    ```powershell
    Copy-Item "settings Example.json" settings.json -Force
    notepad settings.json
    notepad lavalink\application.yml
    ```

    Edit files with your credentials/values according to this [Bot Configuration Guide].

4. **Start Containers** (Build and start the containers)
    ```powershell
    docker compose up -d
    ```

## Configuration Details

### settings.json (essential bits)

```json
{
    "mongodb_url": "mongodb://admin:admin@vocard-db:27017",
    "lavalink": {
        "password": "youshallnotpass"
    }
}
```

### Volume Structure

```
C:\Program Files\vocard\
├── data\
│   └── mongo\              # MongoDB data storage
├── lavalink\
│   ├── application.yml     # Lavalink configuration
│   └── Dockerfile-lavalink # Lavalink Dockerfile
├── settings.json           # Vocard settings
├── Dockerfile              # Vocard Dockerfile (if building from source)
└── docker-compose.yml      # Docker Compose configuration
```

## Management Commands (PowerShell)

Use the following commands to manage your Vocard containers:

-   **Start Services**

    ```powershell
    docker compose up -d
    ```

-   **Stop Services**

    ```bash
    docker compose down
    ```

-   **View Logs**

    ```bash
    docker compose logs -f
    ```

-   **Pull Updates and Restart**
    ```bash
    docker compose pull; docker compose up -d
    ```

## Troubleshooting

### Healthcheck Failures

```powershell
docker compose ps                   # View service status
docker compose logs [service_name]  # View logs for a specific service (e.g., vocard, lavalink)
```

### Common Issues

Usually all container failing to start issues are related to syntax errors or wrong values in configuration.

-   **Command Errors**: On some systems, use `docker-compose` instead of `docker compose`.
-   **Configuration Errors**: Validate `settings.json` and `application.yml` using online tools like [JSONLint](https://jsonlint.com/) or a [YAML validator](https://www.yamllint.com).
-   **Port Conflicts**: Ensure ports `2333` (Lavalink) and `27017` (MongoDB) are not in use.
-   **Missing Tokens**: Double-check that all required tokens are set in `settings.json`.

Revisit the [Bot Configuration Guide] to ensure all steps are followed correctly.

[Bot Configuration Guide]: ../config
