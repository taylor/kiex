kiex - Elixir version manager & builder
====

Kiex allows you to easily build and switch between different Elixir versions.

It supports setting the default (global) Elixir version as well as per shell/project versions.

Everything is self-contained under ~/.kiex.

Usage is based *lightly* on [RVM](http://rvm.io), [kerl](https://github.com/spawngrid/kerl), and [rbenv](https://github.com/sstephenson/rbenv).  

### Install

Prereqs: bash

Run the following to get up and running:

```
curl -qs https://raw.github.com/taylor/kiex/master/install | bash -s
```

which will install in $HOME/.kiex.


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


<script type="text/javascript" src="https://asciinema.org/a/7523.js" id="asciicast-7523" async></script>


### Design philosophy

 * KISS
 * Sane defaults
 * Self-contained
 * Single-purpose


#### Comparison Q&A

How is it like exenv (rbenv)?
 * Super light and simple
 * Focus on installing & managing one piece of software: Elixir

How is it not like exenv?
 * Does not use shims
 * Includes elixir build component

How is it like Kerl?
 * Minimal command set
 * Retrieves, builds, installs and manages different releases

How is it not like Kerl?
 * Not as flexible on install path
 * Dynamically get's release list instead of caching
 * Build and install actions are not separated

How is it like RVM?
 * Sane defaults
 * Uses Unix PATH to manage binary to use

How is it not like RVM? 
 * No function over-loading
 * Does not manage/install extra software and prereqs


### Platforms/Shells tested

Operating Systems:
 * Arch
 * CentOS
 * Debian
 * FreeBSD
 * OS X/Darwin
 * Ubuntu

Shells:
 * bash
 * csh
 * tcsh
 * zsh

Erlang installs:
 * erlang-solutions
 * erlang.org
 * kerl
 * Debian apt, FreeBSD pkg, OS X brew


### Alternatives and References

Alternatives:
 * [exenv](https://github.com/mururu/exenv) + [elixir-build](https://github.com/mururu/elixir-build)
 * [edwb](https://github.com/clutchanalytics/edwb)

Related tools:
 * [kerl](https://github.com/spawngrid/kerl) - Easy building and installing of Erlang/OTP instances
 * [kex](https://github.com/d0rc/kex) - Build any tagged release of Erlang/OTP or Elixir from git
 * [heroku-buildpack-elixir](https://github.com/goshakkk/heroku-buildpack-elixir) - Elixir buildpack for Heroku
   - [heroku-buildpack-erlang](https://github.com/archaelus/heroku-buildpack-erlang) - Erlang/OTP buildpack for Heroku
 * [erln8](https://github.com/metadave/erln8) - Erlang/OTP version manager (builds from git source)
 * [robisonsantos/evm](https://github.com/robisonsantos/evm) - Erlang Version Manager (from erlang.org tarballs)


### Limitations

 * Does not build erlang
 * Does not build Dynamo or any other elixir app
 * Same build directory used for every build (saving space vs keeping build env around)
 * No uninstall option for installed elixir versions
 * No per-directory/project config file.
   - You can hack it in by adding kiex use <version> to .rvmrc or friends ;P

### TODO

 * Maybe print source line with use command
 * Add active command (or similar) to show current elixir
   - Already in list command - this would be the single version
   - Maybe show source line?
 * Add sourceline or similar command to show source line to use?
 * Add uninstall option for installed elixirs
 * Maybe add dynamo install and setup for MIX_PATH
   - how to tie to elixir used? gemset like?
   - use dynamo tags?
 * Look at elixir-build for ideas, collaboration
 
### License

See [LICENSE file](LICENSE)
