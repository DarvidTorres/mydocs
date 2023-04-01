We have at least three files that contain:
1. Declaration of function(s) ([[header files]])
2. Definition of function(s) ([[functions]])
3. Source code (main file that contains the program)

To [[compilation]] we usually compile the definition of the function then compile the actual program.  But if we had many files it'd take long time (and we don't want to do that every time we made some changes to either file); so, we use `Makefile`. 

A Makefile consists of a set of _rules_. A rule generally looks like this:

```
targets: dependencies
	command // Tab indentation matters
	command // Tab indentation matters
	command // Tab indentation matters
```

-   The _targets_ are file names, separated by spaces. Typically, there is only one per rule.
-   The _commands_ are a series of steps typically used to make the target(s). These _need to start with a tab character_, not spaces.
-   The _dependencies_ are also file names, separated by spaces. These files need to exist before the commands for the target are run.

```
blah:
	cc blah.c -o blah
```

This time, try simply running `make`. Since there's no target supplied as an argument to the `make` command, the first target is run. In this case, there's only one target (`blah`). The first time you run this, `blah` will be created. The second time, you'll see `make: 'blah' is up to date`. That's because the `blah` file already exists. But there's a problem: if we modify `blah.c` and then run `make`, nothing gets recompiled.

We solve this by adding a prerequisite:

```
blah: blah.c
	cc blah.c -o blah
```

When we run `make` again, the following set of steps happens:

-   The first target is selected, because the first target is the default target
-   This has a prerequisite of `blah.c`
-   Make decides if it should run the `blah` target. It will only run if `blah` doesn't exist, or `blah.c` is _newer than_ `blah`

# options

`make -f file`: Read the file named file as a makefile (default name should be Make).

[Make options](https://www.gnu.org/software/make/manual/html_node/Options-Summary.html)

[A Simple Makefile Tutorial](https://www.cs.colby.edu/maxwell/courses/tutorials/maketutor/)