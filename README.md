# cyphernode-pier
a pier script management configuration for cyphernode operators


## Installing pier

If you dont have rust 
```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
Feels sketchy?

Get it from https://www.rust-lang.org/tools/install
if you dont trust me :)

After installing cargo:
```
cargo install pier
```
## Setting up a pier for cyphernode

Finally, copy the `pier.toml` file into the root directory of your cyphernode installation.

Note: *Pier commands only work from the folder containing the pier.toml file.*

## Using pier

To see all available commands:
```
pier list
```

To see all available commands with tag filters:

```
# only want proxy related commands
pier list -f proxy

# only want bitcoin related commands
pier list -f bitcoin
```

To run a command

```
# Format: pier <command> <args>
# check version
pier version
```
## Adding your own pier commands

using the `version` command as an example:

```
[scripts.version]
alias='v'
command='''
#/bin/bash

head -10 build.sh | grep CYPHERNODE | grep -oP '".*"' 
exit 0;
'''
description = "print cyphernode version"
tags = ['cn']
```
## Known bugs

The stop and start are a bit buggy. They work but you just wont see any output until the script is done.

pier currently is unable to properly pipe the output log from start.sh and stop.sh, so these two are better off run manually.





