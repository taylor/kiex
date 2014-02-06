kiex
====

elixir env mgr and builder thingy

Kiex allows you to easily build and switch between different elixir releases.

It supports setting elixir version for global default, current shell, and starting a temporary subshell.

It builds and installs elixir releases under ~/.kiex.

Usage is based *lightly* on [RVM](http://rvm.io) and [kerl](https://github.com/spawngrid/kerl).

### Install

To install in $HOME/.kiex run the following:

```
curl -qs https://raw.github.com/taylor/kiex/master/install | bash -s
```

### Usage


List installed versions
 * ``` kiex list ```

List known releases
 * ``` kiex list known ```  (or ``` kiex list releases ```)

Install a known release
 * ``` kiex install 0.11.2 ```

Use specific elixir version
 * ``` kiex use 0.11.2 ``` -- Sets the elixir version for current shell.

Use sub-shell with specific elixir version
 * ``` kiex shell 0.11.2 ``` -- Starts sub-shell with given elixir version.  Exiting shell goes to default.

Set default elixir version
 * ``` kiex default 0.11.2 ```

Uninstall kiex and elixirs
 * ``` kiex implode ``` -- This removes all versions of elixir installed by kiex as well as all kiex components

Upgrade kiex
 * ``` kiex selfupdate ``` -- pull down latest updates for kiex
    - Can also re-curl

### Limitations

 * Does not build erlang
 * Does not build Dynamo or any other elixir app
 * Same build directory used for every build (saving space vs keeping build env around)
 * No uninstall option for installed elixir versions
 * No per-directory/project config file.
   - You can hack it in by adding kiex use <version> to .rvmrc or friends ;P

### TODO

 * Add uninstall option for installed elixirs
 * Maybe add dynamo install and setup for MIX_PATH
   - how to tie to elixir used? gemset like?
   - use dynamo tags?
