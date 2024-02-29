# Getting Started

Vocard is a highly customizable Discord music bot, designed to deliver a user-friendly experience. It offers support for a wide range of streaming platforms including Youtube, Soundcloud, Spotify, Twitch, and more.

## Tutorial
Click on the image below to watch the tutorial on Youtube.

[![Discord Music Bot](https://img.youtube.com/vi/f_Z0RLRZzWw/maxresdefault.jpg)](https://www.youtube.com/watch?v=f_Z0RLRZzWw)

## Requirements

- [Python 3.10+](https://www.python.org){:target="_blank"}
- [Lavalink Server (Requires 4.0.0+)](https://github.com/lavalink-devs/Lavalink){:target="_blank"} 

## Installation

### with git { #with-gif data-toc-label="with gif" }
1. Clone the repository:
    ```
    git clone https://github.com/ChocoMeow/Vocard.git
    ```
2. Go to the directory:
    ```
    cd Vocard
    ```
3. Install required packages, ideally by using a [virtual environment]:
    ```
    python -m pip install -r requirements.txt
    ```

After installing all packages, you must [configure the bot before starting](#configuration).

### with docker <small>recommended</small> { #with-docker data-toc-label="with docker" }

Utilizing the official [Docker image] enables a quick setup, as it conveniently includes all necessary dependencies. To get started, simply pull the image using a terminal command:

=== "Docker Hub"

    ```
    docker pull chocomeow/vocard:v2.6.8
    ```

=== "Github"
    ```
    docker pull ghcr.io/chocomeow/vocard:v2.6.8
    ```
    
    [Docker image]: https://hub.docker.com/

## Configuration

1. Rename `.env Example` to `.env` and [fill all the values].
2. Rename `settings Example.json` to `settings.json` and [customize your settings].
3. Now, you can start your bot with `python main.py`.
    
    [virtual environment]: https://realpython.com/what-is-pip/#using-pip-in-a-python-virtual-environment
    [fill all the values]: /configuration/#settings-up-env
    [customize your settings]: /configuration/#settings-up-settingsjson