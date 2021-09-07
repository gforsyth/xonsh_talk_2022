# Xonsh is a shell

```
ls
ls -l
echo $PATH
ls -l | grep tmp
cap = $(ls)
echo cap   # huh?
echo @(cap) # more on this later
```

# Xonsh is Python

```
1 + 1
2**32

import requests
requests.get("http://google.com")

import numpy
x = numpy.random.random((10, 10))
x @ x
```

`xonsh` uses the `site-packages` of whichever Python it's installed into, so anything you want to import needs to be installed there.

```
for i in range(5):
    # a comment
    if i:
        print(i)
```

As a quick aside, this is a full multi-line prompt.  I'm currently using
$VI_MODE, so I can clean up that code above pretty easily in-line

(but ctrl-x ctrl-e is still an option!)

# Xonsh is also something else

```
for i in range(5):
    echo hi
```

```
for i in range(5):
    echo i
```

```
for i in range(5):
    echo @(i)
```

# The environment
Env-vars are created as you would create a Python assignment

```
$HELLO="hi"
echo $HELLO
```

You can also perform environment lookups, but it's a little different than in `bash`

```
$HOME
${"HOME"}
${"HO" + "ME"}


x = "HOME"
${f"{x}"}

import codecs
${codecs.decode("UBZR", "rot13")}
```

Env-vars are typed and get converted on the fly to play nice
```
echo $PATH
```

This would seem to indicate that $PATH is a colon delimited string of paths, but it's not!

```
$PATH
$PATH.reverse()
$PATH
$PATH.reverse()
$PATH
$PATH.pop(0)
$PATH
$PATH.insert(0, "/opt/miniconda/bin")
```

Any env-var that ends in `PATH` gets treated this way, so `$LD_LIBRARY_PATH`, `$RPATH`, whatever

THe thing to remember here, besides how awesome that just was, is that `xonsh` _IS_ `python`.
Some things look, and even behave, like familiar shell equivalents, but they are Python objects, 
which means that we have the power of Python available to us.

# Back to capturing output 

Remember this strangeness?

```
cap = $(ls)
echo cap   # huh?
echo @(cap) # more on this later
```

Well, now we know what that `@()` is about, but that means that `cap` is a Python object.
So instead of `echo @(cap)` we can just type `cap` or `print(cap)`

And by inspection it's clear that `cap` is a `str`, but just to check `type(cap)`

Which means we can use Python string methods!

```
cap = $(ls)
[x for x in cap.split() if "da" in x]
```

or maybe `grep` is simpler?  It's up to you!

```
cap = $(ls | grep)
cap.split()
```

# Command Pipeline

There's another kind of capture available in `xonsh` that returns more
information about the command you've run

```
cap = !(ls)
```

```
type(cap)
```

```
cap.returncode
cap.output
```

And it's a truthy object! so you can use it for control flow:

```
if !(ls | grep ICO):
    print("There's an uppercase ICO in this directory")
mv favicon.ico favicon.ICO
if !(ls | grep ICO):
    print("There's an uppercase ICO in this directory")
mv favicon.ICO favicon.ico
```


# Aliases

Aliases is a builtin dictionary.

Simple creation

```
aliases["grep"] = "ag"
```

Flags and friends can also be passed in (they get split into a list)

```
aliases["grep"] = "ag -U"
aliases["grep"]
```

Also, though, the value can be a function, in which case calling the alias executes that function.
There are a _lot_ of different options for how to handle `stdin`, `stdout` and friends, but let's keep it simple.

```
aliases["banana"] = lambda: "My spoon is too big\n"
```

# Oddities and other adventures in parsing

Rules of xonsh
1. Python always wins

```
ls -l
```

```
ls = 2
l = 1
ls -l
```

```
del l
ls -l
```

2. Use quotes to escape, not backslashes

```
mkdir "a dir with spaces"
```

3. Use the letter `x` everywhere

# Fun stuff
```
with ${...}.swap({"PATH": $PATH[1:]}):
    which python
```

```
import getpass
with ${...}.swap({"USERPASS": getpass.getpass()}):
    echo $USERPASS
$USERPASS
with ${...}.swap({"USERPASS": getpass.getpass()}):
    pass
```

```
# p-strings!
p = p"."
p.absolute()

# pf-strings!
user = "gil"
p = pf"/home/{user}"
```

```
# regex globbing backticks
g`a*`
```

```
$PROMPT
$PROMPT_FIELDS

import random
$PROMPT_FIELDS["rand"] = lambda: random.randint(0, 50)
$PROMPT += " {rand} "
$PROMPT = $PROMPT[:-8]
```

# If there's time

A brief tour of my repo jumper utility.

# Other stuff

xontribs
