# hs-init

[![Build status](https://secure.travis-ci.org/vrom911/hs-init.svg)](http://travis-ci.org/vrom911/hs-init) [![MIT license](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/vrom911/hs-init/blob/master/LICENSE)

This is tool for creating completely configured production Haskell projects.
Consider that this script is using [`Stack`](http://haskellstack.org) for creating and setting up projects.

## Getting started

### Prerequisites

To start using it make sure you have next tools installed on your machine:
* [`Stack`](http://haskellstack.org)
* [`git`](https://git-scm.com)
* [`hub`](https://github.com/github/hub)

### Installation
Installation process can be done with one simple command:

    $ curl https://raw.githubusercontent.com/vrom911/hs-init/master/install | sh

This will download `hs-init.hs` and then put it in `~/.local/bin` (assuming this folder exists).

After that you can call `hs-init` with required command line options, follow the instructions that will appear, and a new project would be created in a subfolder as well as a repository under your github account.

### Usage

See the basic usage syntax below:
```
hs-init PROJECT_NAME [COMMAND [COMMAND_OPTIONS]] [COMMAND [COMMAND_OPTIONS]]

Available global options:
  -h, --help               Show this help text

Available commands:
  on                       Specify options to enable
  off                      Specify options to disable

Available command options:
  -g, --github             Github integration
  -c, --ci                 CI integration (Travis CI)
  -s, --script             Build script
  -l, --library            Library target
  -e, --exec               Executable target
  -t, --test               Tests
  -b, --benchmark          Benchmarks
```
The options to be enabled/disabled can be specified while running the command. If any of applicable command options wasn't tagged as enabled/disabled then the question will be asked during the work of the script.

For example,
```
  hs-init newProject on -letgc off -b
```
will create fully functional project with library, executable file, tests and create the repository on [github](https://github.com), but benchmarks won't be attached to this one.

But when calling this one
```
  hs-init newProject
```
the tool will ask about every particular option, rather you'd like to have it or not in your project.

### Note
This tool was tested with next settings:

    stack version 1.4.0
    git   version 2.9.3
    hub   version 2.2.9

## Features

If you're running the `hs-init` with all options enabled a project with the following hierarchy will be created:

```
PROJECT_NAME
├── app
│   └── Main.hs
├── benchmark
│   └── Main.hs
├── src
│   └── Lib.hs
├── test
│   └── Spec.hs
├── CHANGELOG.md
├── LICENSE
├── PROJECT_NAME.cabal
├── README.md
├── Setup.hs
├── stack.yaml
├── .git
├── .gitignore
└── .travis.yml
```
and also repository with one commit at master will be added with enabled `Travis-CI` for that.

## Acknowledgments

This project was inspired by [Aelve/new-hs](https://github.com/aelve/new-hs#readme), which is the tool with the same goal but the difference is that it's using [`cabal`](https://www.haskell.org/cabal/) for creating projects.
