kiex - Elixir version manager
====

Kiex allows you to easily build and switch between different [Elixir](http://elixir-lang.org/) versions.

It supports setting the default (global) Elixir version as well as per shell/project versions.

Everything is self-contained under ~/.kiex.

Usage is based *lightly* on [RVM](http://rvm.io), [kerl](https://github.com/spawngrid/kerl), and [rbenv](https://github.com/sstephenson/rbenv).

*NOTE:* Some Erlang source builds are broken.  [See below](#notes).

### Install

**Prerequisites:** bash, curl, erlang, git, make, openssl 

Run the following to get up and running:

```
\curl -sSL https://raw.githubusercontent.com/taylor/kiex/master/install | bash -s
```

which will install in $HOME/.kiex.

### Usage

List installed versions
 * ``` kiex list ```

List known releases
 * ``` kiex list known ```  (or ``` kiex list releases ```)

List current branches
 * ``` kiex list branches ```

Install a known release or branch.
 * ``` kiex install 0.12.5 ```

Use specific elixir version
 * ``` kiex use 0.12.5 ``` -- Sets the elixir version for current shell.

Create an alias for the specified elixir version
 * ``` kiex alias 0.12.5 0.12 ```

Use sub-shell with specific elixir version
 * ``` kiex shell 0.12.5 ``` -- Starts sub-shell with given elixir version. Exiting shell goes to default.

Set default elixir version
 * ``` kiex default 0.12.5 ```

Uninstall kiex and elixirs
 * ``` kiex implode ``` -- This removes all versions of elixir installed by kiex as well as all kiex components

Upgrade kiex
 * ``` kiex selfupdate ``` -- pull down latest updates for kiex
    - Can also re-curl

### Sourcing elixir into your path

After installing your preferred version of elixir and setting it as your default you can use kiex scripts to
put your default elixir bin into your path. One way to do this is to add the following line into your rc file:

```
[[ -s "$HOME/.kiex/scripts/kiex" ]] && source "$HOME/.kiex/scripts/kiex"
```

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
 * Dynamically gets release list instead of caching
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
 * [asdf](https://github.com/HashNuke/asdf) extendable version manager for multiple languages (eg. ruby, erlang, elixir)

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

<a name="notes">

### Notes

Some erlang builds (including default kerl) are unusuable on current CentOS and Fedora distros as a result of an OpenSSL update.  -- 2014/03/31

Various bugs reported:
  * https://bugzilla.redhat.com/show_bug.cgi?id=1023017
  * https://groups.google.com/forum/#!topic/erlang-programming/wW6Uuz4VO2w
  * https://github.com/basho/rebar/issues/375
  * https://bugs.ruby-lang.org/issues/9065

A update to OTP crypto https://github.com/RoadRunnr/otp/commit/8837c1be2ba8a3c123df3f5a87003daa9aac6539

### TODO

 * Merge install script into kiex script as an install function
 * Cleanup build output (extra git info etc)
 * Maybe print source line with use command
 * Add active command (or similar) to show current elixir
   - Already in list command - this would be the single version
   - Maybe show source line?
 * Add sourceline or similar command to show source line to use?
 * Maybe add dynamo install and setup for MIX_PATH
   - how to tie to elixir used? gemset like?
   - use dynamo tags?
 * Look at elixir-build for ideas, collaboration

### License

See [LICENSE file](LICENSE)
