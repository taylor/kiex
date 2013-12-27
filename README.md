kiex
====

elixir builder thingy

Builds and installs elixir under ~/.kiex.  Currently the use command just
displays the "source" line to run.  It can be added to your shell rc file
(.bashrc/.zshrc) or if you have rvm you can add it to .rvmrc :P

### Install

Download kiex and put it somewhere in your path.

To install in $HOME/bin run the following:

```
curl -qs https://raw.github.com/taylor/kiex/master/install | bash -s
```

### Usage


List known releases
 ``` kiex list known ```

List installed releases
 ``` kiex list ```

Install a known release
 ``` kiex install 0.11.2 ```

Use elixir release
 ``` kiex use 0.11.2 ```
