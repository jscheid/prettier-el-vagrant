# Basic Installation of prettier.el

This is a simple installation of `prettier.el` from scratch. Use it as a
reference installation or as a starting point when trying to reproduce an issue.

## Usage

Make sure [Vagrant](https://www.vagrantup.com/) is installed, then run in this
directory:

```shell
vagrant up && vagrant ssh
```

## Details

This installs Emacs Beta via Snap, latest Node via nvm, and latest Prettier
globally via npm. It also installs `markdown-mode`.
