# Nix Installation

Jarvis now has a [Nix] expression for installing Jarvis using
[Nix]. [Nix] is a powerful package manager for Linux and other Unix
systems that makes package management reliable and reproducible. The
recipe works on both Linux and Mac OS X.

## Getting Started with Nix

There are a number of tutorials on getting started with [Nix]. The
page that I used when getting started is on the [Blog of the HPC team
of
GRICAD](https://gricad.github.io/calcul/nix/tuto/2017/07/04/nix-tutorial.html).

I also made [my own
notes](https://github.com/wd15/nixes/blob/master/NIX-NOTES.md), which
are a succinct steps that I use when setting up a new system with
[Nix].

## Installing

Once you have a working [Nix] installation use the
[Nix-shell](https://www.sam.today/blog/environments-with-nix-shell-learning-nix-pt-1/)
to create the environment,

    $ nix-shell --pure

in the base Jarvis directory to create an environment to use Jarvis.

`nix-shell` drops the user into a shell with a working version of
Jarvis. To test your installation use

    $ nix-shell --pure --command "cd jarvis/tests; py.test --ignore=test_vasp.py"

## Additional Packages

To install additional packages available from Nixpkgs include them in
the `buildInputs` list in `default.nix`.

## Using Pip

Packages unavailable from [Nix] can be installed using `pip`. In this
case, the installation has been set up so that the [Nix] shell knows
about a `.local` directory in the base Jarvis directory used by `pip`
for installation.  So, for example, to install the `toolz` package
from within the [Nix] shell use:

    $ pip install --user toolz

The `.local` directory will persist after the [Nix] shell has been
closed.

[Nix]: https://nixos.org/nix/