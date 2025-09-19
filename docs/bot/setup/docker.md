# Docker Installation Guide for Vocard with Installer

This guide simplifies the installation of Vocard using Docker with a installer. Follow the steps below to set up Vocard quickly and easily.

## Prerequisites

1. **Install Python and Docker**: Ensure you have Python and Docker (with Docker Compose) installed on your system.

   - For Docker installation instructions, refer to the [official guide](https://docs.docker.com/engine/install/).
   - For Docker Compose installation, refer to the [official guide](https://docs.docker.com/compose/install/).

   Verify the installations:

   ```bash
   python --version
   docker --version
   docker compose version
   ```

## Installation Steps

### Step 1: Download the Installer Script

Use the command appropriate for your operating system to download the installer script from GitHub.

- **For Windows**:

  ```powershell
  Invoke-WebRequest -Uri https://raw.githubusercontent.com/ChocoMeow/Vocard-Installer/refs/heads/main/installer.py -OutFile installer.py
  ```

- **For Linux and Mac**:

  ```bash
  curl -L -o installer.py https://raw.githubusercontent.com/ChocoMeow/Vocard-Installer/refs/heads/main/installer.py
  ```

### Step 2: Install Required Python Packages

Make sure to install the necessary Python package:

```bash
python -m pip install PyYAML
```

### Step 3: Run the Installer

Execute the installer script:

```bash
python installer.py
```

### Step 4: Follow the Installation Instructions

Carefully follow the prompts provided by the installer to complete the setup.

## Post-Installation Steps

Once the installation is complete, verify your Vocard installation and start the containers:

### Start Vocard Containers

```bash
docker compose up -d
```

### Manage Services

You can manage your Vocard services with the following commands:

- **Start Services**:

  ```bash
  docker compose up -d
  ```

- **Stop Services**:

  ```bash
  docker compose down
  ```

- **View Logs**:

  ```bash
  docker compose logs -f
  ```

- **Pull Updates and Restart**:

  ```bash
  docker compose pull && docker compose up -d
  ```

## Troubleshooting

### Checking Service Status

If containers fail to start, use:

```bash
docker compose ps                   # View service status
docker compose logs [service_name]  # View logs for a specific service (e.g., vocard, lavalink)
```

### Common Issues

- **Command Errors**: On some systems, use `docker-compose` instead of `docker compose`.
- **Configuration Errors**: Validate your configuration files using online tools like [JSONLint](https://jsonlint.com/) for JSON or [YAML Lint](https://www.yamllint.com) for YAML.
- **Port Conflicts**: Ensure ports `2333` (Lavalink) and `27017` (MongoDB) are not in use.
- **Missing Tokens**: Double-check that all required tokens are set in your configuration files.

For further assistance, refer to the [Bot Configuration Guide] to ensure all steps are followed correctly.

[Bot Configuration Guide]: ../config/index.md