# EdPy
Microbric Edison robot using a subset of Python 2

This software is a service used by the EdPy web application to take a subset of python 2 and create a wav file which can be downloaded to a Microbric Edison robot.
As it is a service which the web-app uses it is strictly command line!

There are a couple of main python programs:

* EdPy.py -- this will take a file of an edpy program, and compile, assembler and create a wav file for download
* EdAsm.py -- this tool can be used to assemble an assembler source file. EdPy.py does this and more! It is
  still available for working directly with the TASM assembler language
* TranStrings.py -- a tool to find all translatable strings and make sure they are used correctly. This will 
  be used when we start the translation effort
  
All of these programs must be run using python 2.7 or later, but NOT python 3.0 or later.
So it is a python 2 program, which uses some python 2.7 additions but it isn't cleanly python 3.0.
All new code was developed using future statements to use new print functionality and import functionality so should be easy to go to python 3. But some code was taken from EdWare (token assembler bits) so it will need more work.

All of the main python programs have a 'help' option -- e.g. python2 EdPy.py --help.

## Install pyenv

As `python2` is less and less available on different operating systems you can use the `pyenv` tool to make it available locally.

```
brew install pyenv
pyenv install 2.7.18
alias python2=$HOME/.pyenv/versions/2.7.18/bin/python2.7
```

## Examples

To get help:

```
python2 src/EdPy.py --help
```

To compile a program:

```
python2 src/EdPy.py src/en_lang.json examples/test_program.py
```

To just check a program. This doesn't generate a wav file.

```
python2 src/EdPy.py -c src/en_lang.json examples/test_program.py
```

Turn on debugging output and get an assembler listing

```
python2 src/EdPy.py -d 2 -a test.lst src/en_lang.json examples/test_program.py
```
