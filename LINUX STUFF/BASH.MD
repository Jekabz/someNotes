# BASH

###### control keys

ctrl+c -- stops current command, with cleaning
ctrl+\ -- same as above but with force, no cleaning
ctrl+z -- pause current command
ctrl+d -- end of input (QUIT)
esc+/ -- same as tab autocomplete, but only for filenames
ctrl+l -- same as clear
----
ctrl+o
  * With up arrow go to desired command
  * ctrl+o
  * you are given the next command in line
  * profit!

#### configuration files:

###### .bash_profile
###### .bash_logout
###### .bashrc

#### variables
* by convention, built in variables ar UPPER CASSE
* `varname=value` -- *defines variable, no space between or after =*
* if variable contains several words, it has to be in single quotes
* to refer to a variable, precede its name with $

$HISTSIZE -- *how many commands are saved in history*
`cd -` -- *goes back one directory*
