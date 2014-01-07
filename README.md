kiex
====

elixir builder thingy

Builds and installs elixir releases under ~/.kiex.

Usage is based *lightly* on [RVM](http://rvm.io) and [kerl](https://github.com/spawngrid/kerl).

### Install

Download kiex and put it somewhere in your path.

To install in $HOME/bin run the following:

```
curl -qs https://raw.github.com/taylor/kiex/master/install | bash -s
```

### Usage


List installed releases
 * ``` kiex list ```

List known releases
 * ``` kiex list known ```  (or ``` kiex list releases ```)

Install a known release
 * ``` kiex install 0.11.2 ```

Use specific elixir version
 * ``` kiex use 0.11.2 ``` -- Displays shell command to use for current shell.  Exiting shell goes to default.

Use sub-shell with specific elixir version
 * ``` kiex shell 0.11.2 ``` -- Starts sub-shell with given elixir version.  Exiting shell goes to default.

Set default elixir version
 * ``` kiex default 0.11.2 ```

Uninstall kiex and elixirs
 * ``` kiex implode ``` -- This removes all versions of elixir installed by kiex as well as all kiex components


### Limitations

 * Does not build erlang
 * Does not build Dynamo or any other elixir app
 * Same build directory used for every build (saving space vs keeping build env around)
 * The ``` use ``` command just displays the *source* command line to run
   - It can be added to any startup script including .rvmrc :P
 * No uninstall option for installed elixir versions

### TODO

 * Add uninstall option for installed elixirs
