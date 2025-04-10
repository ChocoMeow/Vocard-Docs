# Setup Guide

## Install Python
- Vocard Dashboard requires Python 3.11 or higher.
- Follow the guidelines here: [Installing Python].

## Download Vocard Dashboard

### with docker <small>recommended</small> { #with-docker data-toc-label="with docker" }

Utilizing the official [Docker image] enables a quick setup, as it conveniently includes all necessary dependencies. To get started, simply pull the image using a terminal command:

=== "Github"
    ```
    docker pull ghcr.io/chocomeow/vocard-dashboard:latest
    ```

1.  [Configure the bot](#configuration) before starting the docker containers.
2.  Start the Docker containers in detached mode:
    ```
    docker-compose up -d
    ```
    
### with git { #with-gif data-toc-label="with gif" }
1. Clone the repository:
    ```
    git clone https://github.com/ChocoMeow/vocard-dashboard.git
    ```
2. Go to the directory:
    ```
    cd Vocard Dashboard 
    ```
3. Install required packages, ideally by using a [virtual environment]:
    ```
    python -m pip install -r requirements.txt
    ```

After installing all packages, you must [configure the bot before starting](#configuration).

## Configuration

1. Rename `settings Example.json` to `settings.json` and [customize your settings].
2. Now, you can start your bot with `python main.py`.
    
    [Docker image]: https://docs.docker.com/get-started/
    [virtual environment]: https://realpython.com/what-is-pip/#using-pip-in-a-python-virtual-environment
    [customize your settings]: ../config/
    [Installing Python]: ../setup/installing-python/