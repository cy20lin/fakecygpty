fakecygpty
============

Introduction
------------
This package supplies cygwin's pty feature for NTEmacs.
If you want to use the command requires pty such as `bash`, try this.

* `shell-mode` or `ansi-term` with cygwin's shell like `bash` will be run correctly.
* I/O buffer on `gdb-mode` will be run correctly than native one.
* `signal-process' can send arbitrary signals, except it was called interactively.

Installation
------------

Compile `fakecygpty.c` and `qkill.c` on cygwin enviroment:

    gcc -o fakecygpty fakecygpty.c
    gcc -o qkill qkill.c

And copy *.exe into somewhere on you $PATH.

If `autoreconf` package is installed, you can use configure script:

    autoreconf -ivf && ./configure && make install

`fakecygpty.el` isn't installed automatically. put into your `load-path` by self.

How to use
----------
If you want to activate only to a specific program, rename `fakecygpty.exe` to
`f_TARGET.exe` like `f_ssh.exe`, and invoke it.

If you want to apply to all, put below into your `init.el`:

    (require 'fakecygpty)
    (fakecygpty-activate)

And if you want to disable `fakecygpty` temporary, type `M-x disable-fakecygpty`.

Customizing
-----------

### Ignored programs
Some program using Windows native console, such as `cmd.exe`, don't work well
with `fakecygpty.exe`.

`fakecygpty-ignored-program-regexps`: Set regexp list of program name that
you don't want to apply `fakecygpty`.

### Path of programs

* `fakecygpty-program`: Path of `fakecygpty.exe`.
* `fakecygpty-qkill-program`: Path of `qkill.exe`.
