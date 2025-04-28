# Setup Guide

## Install Python

-   Vocard requires Python 3.11 or higher.
-   Follow the guidelines here: [Installing Python].

## Download Vocard Bot

### With Docker <small>recommended</small> { #with-docker data-toc-label="with docker" }

Using the official [Docker image](https://ghcr.io/chocomeow/vocard) is the easiest way to set up Vocard, as it includes all necessary dependencies. Follow the platform-specific guide below to get started:

-   For **Linux**, follow the [Docker Setup Guide for Linux](docker-linux.md).
-   For **Windows**, follow the [Docker Setup Guide for Windows](docker-windows.md).

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

## Configuration

1. Rename `settings Example.json` to `settings.json` and [customize your settings].
2. Now, you can start your bot with `python main.py`.

    [Docker image]: https://docs.docker.com/get-started/
    [virtual environment]: https://realpython.com/what-is-pip/#using-pip-in-a-python-virtual-environment
    [customize your settings]: ../config/
    [Installing Python]: ../setup/installing-python/