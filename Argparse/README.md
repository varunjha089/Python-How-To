# Argparse Tutorial

This tutorial is intended to be a gentle introduction to *`argparse`*, the recommended command-line parsing module in the Python standard Library.

There are two other modules that fulfill the task
- **`getopt`** :- an equivalent for **`getopt()`** from the C Programming Language
- **`optparse`** :- is a deprecated module. **`Argparse`** is based on **`optparse`**, and is similar in use.

## Python file Description


| S. No. | Content | Description | Link |
|---|---|---|---|
| 01 | 01.py    | Basic                                                       | [Link](01.py/)    |
| 02 | 02.py    | Introducing Positional Arguments                            | [Link](02.py/)    |
| 03 | 02_1.py  | Introducing Positional Arguments whith **`help`**           | [Link](02_1.py/)  |


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

```py
import argparse

parser = argparse.ArgumentParser()
parser.add_argument("echo")
args = parser.parse_args()
print(args.echo)
```

And the running code

```console
ubuntu@ip:~$python 02.py 
usage: 02.py [-h] echo
02.py: error: the following arguments are required: echo

ubuntu@ip:~$ python 02.py --help
usage: 02.py [-h] echo

positional arguments:
  echo

optional arguments:
  -h, --help  show this help message and exit

ubuntu@ip:~$ 
```

What is happening here:
- The **`add_argument()`** method is used to specify which command-line options the program is willing to accept.
- Calling our program now requires us to specify an option.
- The **`parse_args()`** method actually returns some data from the options specified, in this case, **`echo`**.
- The variable is some form of "magic" that **`argparse`** performs for free. You will also notice that its name matches the string argument given to the method, **`echo`**.

```console
ubuntu@ip:~$ python 02_1.py --help
usage: 02_1.py [-h] echo

positional arguments:
  echo        Echo the string you use here.

optional arguments:
  -h, --help  show this help message and exit

ubuntu@ip:~$ 
```

Little more functionality:

```py
import argparse

parser = argparse.ArgumentParser()
parser.add_argument("square", help="Display the square of a given number.")
args = parser.parse_args()
print(args.square**2)
```

Result of above code

```console
ubuntu@ip:~$ python 02_2.py 5
Traceback (most recent call last):
  File "02_2.py", line 7, in <module>
    print(args.square**2)
TypeError: unsupported operand type(s) for ** or pow(): 'str' and 'int'

ubuntu@ip:~$ 
```

This didn't go so well because the **`argparse`** treats the options we give it as string, unless we tell it otherwise. So, the correct code will be:

```py
import argparse

parser = argparse.ArgumentParser()
parser.add_argument("square", help="Display the square of a given number.", type= int)
args = parser.parse_args()
print(args.square**2)
```

```console
ubuntu@ip:~$ ppython 02_2.py 5
25

ubuntu@ip:~$
```

