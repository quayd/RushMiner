# Wishlist and Improvements for RushMiner

## Intended Additions
* API for remote queries
* Native voltage control
* Remote live command line: send "--ftdi-cmd=..." with scripting to a live running instance of RushMiner using standard utilities. 
* Stats on individual cores.
* Hotkey to set specific clock value.
* --ftdi-cmd's that take a --no-block can't currently be sequenced with successive --ftdi-cmd's. Add a way to not initiate a command until a specific command (non-block or otherwise) completes.
* In TUI version, fill tabs with extended information on devices, cores, pools, etc. and allow selecting and running commands on various items.
* Complete config file support.
* Use launch configuration files as alternative to existing bash script format.
## Intended Improvements
* Documentation of usage and views.
* Cleaner layout of stats.
* Auto-adjust settings to maintain temperature and/or error rate.
* Run "--ftdi-cmd" on limit: ex. `--ftdi-cmd="--max-temp-action ramp..."
* Reduce and clean up logging information at each level.
* Use consistent device short naming in logs.
## Intended Fixes
* Disconnect handling. Currently there are a couple situations that can go into crazy loops display a stream of errors.
* With a large device count 20+(?) hotkeys can get very slow to respond.
* TCP/IP devices require a second `--ftdi-cmd="monitor ..." or ramp up fails.
* Printing on ramping live, makes it look like clock value jumped straight, skipping in between values
## Community Suggested Additions

## Community Suggested Improvements
