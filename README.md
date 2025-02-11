This is pyrepl, a readline-a-like in Python.

It requires python 2.7 (or newer) and features:

 * sane multi-line editing
 * history, with incremental search
 * completion, including displaying of available options
 * a fairly large subset of the readline emacs-mode keybindings
   (adding more is mostly just a matter of typing)
 * a liberal, Python-style, license
 * a new python top-level
 * no global variables, so you can run two or more independent readers
   without having their histories interfering.
 * no hogging of control -- it should be easy to integrate pyrepl into
   YOUR application's event loop.
 * generally speaking, a much more interactive experience than readline
   (it's a bit like a cross between readline and emacs's mini-buffer)
 * unicode support (given terminal support)

There are probably still a few little bugs & misfeatures, but _I_ like
it, and use it as my python top-level most of the time.

To get a feel for it, just execute:

```shell
$ python pythoni
```

(One point that may confuse: because the arrow keys are used to move
up and down in the command currently being edited, you need to use ^P
and ^N to move through the history)

If you like what you see, you can install it with the familiar

```shell
$ python setup.py install
```

which will also install the above "pythoni" script.

## summary

### Summary of 0.8.4:

 + python3 support
 + support for more readline hooks
 + backport various fixes from pypy
 + gracefully break on sys.stdout.close()

### Summary of 0.8.3:

 + First release from new home on bitbucket.
 + Various fixes to pyrepl.readline.
 + Allow pyrepl to run if unicodedata is unimportable.


### Summary of 0.8.2:

 + This is the same version which is distributed with PyPy 1.4, which uses it
   as its default interactive interpreter:

     - have the possibility of having a "CPython-like" prompt, with ">>>" as
       PS1 and "..." as PS2

     - add the pyrepl.readline module, which exposes a subset of CPython's
       readline implemented on top of pyrepl

 + Add support for colored completions: see e.g. fancycomplete:
   http://bitbucket.org/antocuni/fancycompleter

### Summary of 0.8.1:
 + Fixes
   - in the area of unbound keys and unknown commands
   - in quoted-insert
   - in unicode support
 + make Reader and subclasses new-style classes
   - needed to slightly change the way keymaps are built
   - make the inheritance hierachy look like this
     - Turns out I've been wanting new-style classes since before they existed!
```
                     Reader
                    /      \
      HistoricalReader   CompletingReader
                    \      /
                PythonicReader
```

### Summary of 0.8.0:
 + A whole bundle of things.
   - unicode support (although working out what encoding the terminal
     is using can be "tricky")
   - internal rearchitecting
   - probably a bunch of new bugs...
 + Development and web-presence moved to codespeak.net

### Summary of new stuff in 0.7.1:
 + A non-broken setup.py...

### Summary of new stuff in 0.7.0:
 + Moved to a package architecture.
 + Wrote a (very simple!) distutils setup.py script.
 + Changed the keyspec format to be more sensible.  See the docstring
   in pyrepl/keymap.py for more information.
 + Portability fixes.
 + Various tortuous changes to use 2.2 features where possible but
   retaining 2.1 support (I hope; haven't got a 2.1 here to test with).
 + Jumping up and down on control-C now shouldn't dump you out of
   pyrepl (via a large hammer kind of approach).
 + Bug fixes, particularly in the history handling stuff.
 + reader.Reader has a new method, bind(), intended to be used by the
   user.
 + Changes to the init file handling.
 + Sundry code reorganization.  Libraries built on top of pyrepl will
   probably require small modifications (but I'm not sure anyone has
   written any of these yet!).
 + A prototypical pygame console.

### Other versions summary

 see CHANGES for more details and older news
