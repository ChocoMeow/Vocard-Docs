# Docker Installation Guide for Vocard on Linux

This guide explains how to set up and run Vocard using Docker on a Linux system. Follow the steps carefully to ensure a smooth installation.

## Prerequisites

-   **Docker**: Install Docker using the [official guide](https://docs.docker.com/engine/install/).
-   **Docker Compose**: Install Docker Compose using the [official guide](https://docs.docker.com/compose/install/).

Ensure both are installed and running before proceeding:

```bash
docker --version
docker compose version
```

## Installation Options

Choose one of the following methods to install Vocard. **Method 1 (Pre-built Images)** is recommended for most users due to its simplicity.

### Method 1: Using Pre-built Images <small>recommended</small>

1.  **Create Project Directory**

    ```bash
    mkdir -p /opt/vocard/lavalink
    cd /opt/vocard
    ```

2.  **Download Configuration Files**

    !!! warning "Warning"

         Existing files will be overwritten.

    ```bash
    wget -O settings.json https://raw.githubusercontent.com/ChocoMeow/Vocard/main/settings%20Example.json
    wget -O lavalink/application.yml https://raw.githubusercontent.com/ChocoMeow/Vocard/main/examples/application.yml
    wget -O lavalink/Dockerfile-lavalink https://raw.githubusercontent.com/ChocoMeow/Vocard/main/lavalink/Dockerfile-lavalink
    wget -O docker-compose.yml https://raw.githubusercontent.com/ChocoMeow/Vocard/main/docker-compose.yml
    ```

3.  **Edit Configuration Files**
    Copy and modify the example configurations:

    ```bash
    cp settings.json settings.json.bak
    nano settings.json
    nano lavalink/application.yml
    ```

    Update the files with your credentials and settings as described in the [Bot Configuration Guide].

4.  **Verify Configuration**

    - Ensure ports in `docker-compose.yml` match those in `settings.json` and `application.yml`. Defaults are:
        - Lavalink: `2333`
        - MongoDB: `27017`
    - Vocard uses a local Docker network, so ports are not exposed publicly unless modified.
    - Verify all mandatory tokens are set in `settings.json`.

5.  **Start Containers**
    ```bash
    docker compose up -d
    ```

### Method 2: Build from Source

1. **Clone the Repository**

    ```bash
    git clone https://github.com/ChocoMeow/Vocard.git
    cd Vocard
    ```

2. **Configure Docker Compose**
   Edit `docker-compose.yml` to build from source:

    - Uncomment the `build` sections for `vocard` and `lavalink` services.
    - Comment out the `image` lines.

    Example for `vocard` service:

    ```yaml
    vocard:
        # image: ghcr.io/chocomeow/vocard:latest
        build:
            dockerfile: ./Dockerfile
    ```

3. **Edit Configuration Files**
   Copy and modify the example configurations:

    ```bash
    cp settings\ Example.json settings.json
    nano settings.json
    nano lavalink/application.yml
    ```

    Update the files with your credentials and settings as described in the [Bot Configuration Guide].

4. **Build and Start Containers**
    ```bash
    docker compose up -d
    ```

## Configuration Details

### Essential Settings

#### settings.json

Ensure the MongoDB URL and Lavalink password are correctly set:

```json
{
    "mongodb_url": "mongodb://admin:admin@vocard-db:27017",
    "lavalink": {
        "password": "youshallnotpass"
    }
}
```

#### Project Directory Structure

```shell
Vocard/
├── data/
│   └── mongo/              # MongoDB data storage
├── lavalink/
│   ├── application.yml     # Lavalink configuration
│   └── Dockerfile-lavalink # Lavalink Dockerfile
├── settings.json           # Vocard settings
├── Dockerfile              # Vocard Dockerfile (if building from source)
└── docker-compose.yml      # Docker Compose configuration
```

## Managing Services

Use the following commands to manage your Vocard containers:

-   **Start Services**

    ```bash
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
    docker compose pull && docker compose up -d
    ```

## Troubleshooting

### Checking Service Status

If containers fail to start:

```bash
docker compose ps                   # View service status
docker compose logs [service_name]  # View logs for a specific service (e.g., vocard, lavalink)
```

### Common Issues

-   **Command Errors**: On some systems, use `docker-compose` instead of `docker compose`.
-   **Configuration Errors**: Validate `settings.json` and `application.yml` using online tools like [JSONLint](https://jsonlint.com/) or a [YAML validator](https://www.yamllint.com).
-   **Port Conflicts**: Ensure ports `2333` (Lavalink) and `27017` (MongoDB) are not in use.
-   **Missing Tokens**: Double-check that all required tokens are set in `settings.json`.

Revisit the [Bot Configuration Guide] to ensure all steps are followed correctly.

[Bot Configuration Guide]: ../config/