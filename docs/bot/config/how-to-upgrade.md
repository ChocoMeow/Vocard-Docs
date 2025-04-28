# How to upgrade

!!! warning "Warning"

    Please note that the bot directory does not contain any personal 
    files before running the update command. Any such files will be
    deleted upon execution.
  
Check the current version

```
python update.py -c
```

Install the latest version

```
python update.py -l
```

Install the specified version

```
python update.py -v VERSION
```

Install the beta version

```
python update.py -b
``` 

Install the Migration Script

To install the migration script (note that this does not include every version), you can review the scripts in the [Vocard-Migration repository](https://github.com/ChocoMeow/Vocard-Magration):
```
python update.py -m
``` 