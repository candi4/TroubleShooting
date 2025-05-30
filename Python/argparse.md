# argparse
Parsing arguments entered from the command line.    
Reference: [argparse documentation](https://docs.python.org/3/library/argparse.html)

## Basic
```python
# basic.py
import argparse

parser = argparse.ArgumentParser(description="Setting for training")
parser.add_argument('-g', '--gpunumber', help="Select number for GPU", type=int, default=0)
parser.add_argument('--verbose', action='store_true', help='Print detailed message')

args = parser.parse_args()
config = vars(args) # dict
gpunumber = args.gpunumber
verbose = args.verbose
```
```shell
python basic.py                         # gpunumber=0; verbose=False
python basic.py -g 3                    # gpunumber=3; verbose=False
python basic.py --gpunumber 3           # gpunumber=3; verbose=False
python basic.py --gpunumber 3 --verbose # gpunumber=3; verbose=True
```

### Test in python
parse_args

## add_argument: `action`
The action keyword argument specifies how the command-line arguments should be handled.    

| `action` Value      | Description |
|---------------------|-------------|
| `'store'` (default) | Stores the argument value as-is. |
| `'store_true'`      | Stores `True` if the argument is present, otherwise stores `False` (used for flags). |
| `'store_false'`     | Stores `False` if the argument is present, otherwise stores `True`. |
| `'append'`          | Appends the argument value to a list (if the option is used multiple times). |
| `'count'`           | Counts how many times the option appears. |
| `'help'`            | Automatically displays a help message and exits. |
| `'version'`         | Displays version information and exits. |

Only actions that consume command-line arguments (e.g. 'store', 'append' or 'extend') can be used with positional arguments.
### `'store'` 
This just stores the argument’s value. This is the default action.
### `'store_const'`
This stores the value specified by the const keyword argument; note that the const keyword argument defaults to None. The 'store_const' action is most commonly used with optional arguments that specify some sort of flag.
### `'store_true'` and `'store_false'`
These are special cases of 'store_const' used for storing the values True and False respectively. In addition, they create default values of False and True respectively
```python
store_true
```
### `'append'`
This stores a list, and appends each argument value to the list. It is useful to allow an option to be specified multiple times. If the default value is non-empty, the default elements will be present in the parsed value for the option, with any values from the command line appended after those default values.
### `'append_const'`
This stores a list, and appends the value specified by the const keyword argument to the list; note that the const keyword argument defaults to None. The 'append_const' action is typically useful when multiple arguments need to store constants to the same list. 
### `'extend'`
This stores a list and appends each item from the multi-value argument list to it. The 'extend' action is typically used with the nargs keyword argument value '+' or '*'. Note that when nargs is None (the default) or '?', each character of the argument string will be appended to the list. 
### `'count'`
This counts the number of times a keyword argument occurs. For example, this is useful for increasing verbosity levels
### `'help'`
This prints a complete help message for all the options in the current parser and then exits. By default a help action is automatically added to the parser. See ArgumentParser for details of how the output is created.
### `'version'`
This expects a version= keyword argument in the add_argument() call, and prints version information and exits when invoked:

Reference: [argparse documentation #action](https://docs.python.org/3/library/argparse.html#action)

## add_argument: `dest`
```python
# example.py
import argparse

parser = argparse.ArgumentParser()
parser.add_argument('--save-image', action='store_true', default=True,
                    help="Save images while training. Disable with --no-save-image.")
parser.add_argument('--no-save-image', dest='save_image', action='store_false',
                    help="Do not save images while training.")
args = parser.parse_args()

save_image = args.save_image
```
```shell
python example.py                 # save_image = True
python example.py --save-image    # save_image = True
python example.py --no-save-image # save_image = False
```
* The `default` parameter is used to avoid conflicts between options.

## add_argument: `nargs`
```python
# example.py
import argparse

parser = argparse.ArgumentParser()
parser.add_argument('-l', '--lr-scale', nargs=2, metavar=('START', 'END'),
                    help="Start and end scale factors to multiply default learning rate",
                    type=float, default=[1.0, 1.0])
args = parser.parse_args()

lr_scale = args.lr_scale
```
```shell
python example.py # lr_scale = [1.0, 1.0]
python example.py --lr-scale 4.0 3 # lr_scale = [4.0, 3.0]
```

## Tips
### Naming
Any internal `-` characters will be converted to `_` characters to make sure the string is a valid attribute name.
```python
# example.py
import argparse

parser = argparse.ArgumentParser()
parser.add_argument('--foo-bar')
args = parser.parse_args()

foo_bar = args.foo_bar
```
```shell
python example.py --foo-bar apple # foo_bar='apple'
```