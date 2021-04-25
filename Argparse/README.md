# Argparse Tutorial

This tutorial is intended to be a gentle introduction to *`argparse`*, the recommended command-line parsing module in the Python standard Library.

There are two other modules that fulfill the task
- **`getopt`** :- an equivalent for **`getopt()`** from the C Programming Language
- **`optparse`** :- is a deprecated module. **`Argparse`** is based on **`optparse`**, and is similar in use.

## Basic

The basics of argument parsing is as follows.

```py
import argparse

parser = argparse.ArgumentParser()
parser.parse_args()
```

```console
ubuntu@ip:~$ python 01.py  --help
usage: 01.py [-h]

optional arguments:
  -h, --help  show this help message and exit

ubuntu@ip:~$ 
```

What is happening here:
- Running the script without any options results is nothing displayed to stdout. Not so useful.
- The second one starts to display the usefulness of the **`argparse`** module. We have done almost nothing, but already we get a nice help message.
- The **`--help`** option, which can also be shortened to **`-h`**, is the only option we get without specifying it.

[Python File](o1.py)

## Introducing Positional Arguments.

