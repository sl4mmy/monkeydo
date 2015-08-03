# monkeydo
`monkeydo` is a command line utility for automatically running other command
line utilities.  It aggregates and pretty-prints the output from each command
line utility, and propagates signals to each so that it is possible to manage
and control multiple processes like a single process.

# 10 second tutorial
    $ cat >monkey.do <<EOF
    exec start_database_server.sh
    exec start_application_server.sh
    exec start_web_server.sh
    EOF
    $ run
    ...Lots of output...
    ^C  # <-- terminates monkeydo and all three child processes
    $

# Can't you already do that with shell scripts?
Yep!  Shell scripts can provide all the functionality of `monkeydo`.

## And Makefiles?
Definitely!  Makefiles can also do everything that `monkeydo` does.

## So...
What's the point of `monkeydo`?  Simple.

No, I mean: `monkeydo` is simple.  It makes it easy and convenient to do all
that stuff.

In order to reproduce the functionality of `monkeydo` in a shell script you
would have to write a lot of shell code, some of it using advanced shell
scripting techniques like arrays and trap.  It's not complicated, but it's a
fair bit of work.  And you would have to repeat that work in every shell script
where you wanted that type of functionality.

Ditto Makefiles.

I totally encourage you to do so, by the way.  (Reproduce the functionality of
`monkeydo` in your shell scripts or Makefiles, that is).  It's good experience
and a valuable learning opportunity.  I bet you'll pick up several new tricks
along the way that you can use to make all of the other shell scripts and
Makefiles that you write better.

And don't worry, it's not like I'll be offended if you decide not to use
`monkeydo`.  If your projects already have a lot of scripting and automation,
if your build scripts already contain a bunch of convenience targets for
automating common tasks, then by all means skip `monkeydo` and roll your own
solution.

But if you don't already have all that scripting and automation in place then
I think `monkeydo` is the simplest and quickest way to introduce this
functionality into your project.  And since that's the whole point of `monkeydo`
in the first place, if your `monkeydo` experience is difficult or complicated or
painful then I would love to hear your feedback (preferably in the form of a
GitHub issue or pull request).

# Ok, sounds interesting, where can I learn how to try it for myself?
The documentation is distributed with `monkeydo` and is automatically installed
on your system when you install`monkeydo` (see next section below).

To read about the config file syntax understood by `monkeydo` see `monkeydo(5)`
(i.e. run `man 5 monkeydo` at the command line).  To read about the `run`
command itself, including all of its command line arguments, see `run(1)` (i.e.
run `man 1 run` at the command line).

# Installing the official package for your system
Well, first you need to encourage the developers of your system to build an
official package of `monkeydo`.  Then you will be able to use your system's
regular package management tools to install `monkeydo`, e.g.

#### On OpenBSD
    $ pkg_add monkeydo

#### On Arch Linux
    $ pacman -S monkeydo

#### On Debian & Ubuntu
    $ apt-get install monkeydo

#### On RPM-based distros
    $ yum install monkeydo

#### On Mac OS X using home brew
    $ brew install monkeydo

#### Don't see your preferred system listed here?
Send me a pull request!

# Installing from source
    $ test -d build || build
    $ cd build/ && ../configure --prefix=/usr/local
    $ make
    $ make test # <-- Optionally verify that everything works as expected
    $ make install
