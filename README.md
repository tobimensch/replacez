# Install

Just download replacez from this repository and put it somewhere in your PATH. You're done.

Unless you don't have python, then you need to get python first. And also the docopt module.

# Description

User interface for editing and applying small python scripts that convert individual lines in a file or from stdin
however the user wants and by whatsoever method is available through python including regex, parsers,
string manipulation, calling subprocesses and everything else.

While the usual command line based suspects like sed are great for many tasks, sometimes you need several lines of
code and a mix between different methods of conversion like custom parsers and regex to tackle a problem.

Replacez first reads all the lines from a file or stdin, then it selects a subset of matching lines according
to the regex given by the -m, --line-match option. If --line-match isn't given, replacez works on all lines.

For all matching lines replacez creates an empty template python script, which will be called for every individual
line and each line will then be replaced by the output of the script.

The script has one input variable "line", on which the user can use all the power of python to transform it.

# How it's used

You call replacez with a filename and the optional --line-match regex.

    replacez myclass.cpp --line-match ".*std::string.*"

This example would match all the lines containing std::string in a cpp file.

Now an editor should open and the console interface looks like this:

    [0]:

The editor starts with the empty python template. If you close it, you get back to the console.
Type `h` or `help` to get all the commands available. 

```
-----------------------------------[help])------------------------------------
z|[default]    start editor
v|view         view all matched lines in original state
0|apply        view all matched lines with user's replacing applied
g|goto         goto matched line. prompts you for a number. see numbers with (v) or (0)
e|editor       set editor
w|write        write to file. prompts user for filename [defaults to: --output FILE or <FILE>.replacez]
q|quit         quit
h|help         view this help
------------------------------------------------------------------------------

```

To get back to the editor any non-specified key works or z.
To view the result on the matched lines after saving your script type 0.

If your script does what you want it to do, you can save the file to disk using `w`.

All the unmatched lines will also be saved, but of course without changes to them.

# CLI

```
usage: replacez [options] <FILE>

replace or modify text lines from a file or stdin using python 

Options:
  -m REG, --line-match REG    only work on lines matching regex
                              i.e ".*CHECK_EQUAL.*"
  -e FILE, --editor FILE       set your favorite editor
  -o FILE, --output FILE      file to write to
  -h, --help                  show this help message and exit
  -v, --version               display version information
```


# Bugs / Development / Testing / Feedback

The github issues page of replacez is the right place for all of that:
https://github.com/tobimensch/replacez/issues

