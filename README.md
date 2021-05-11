# Alt::ExtUtils::PkgConfig::PLICEASE ![linux](https://github.com/plicease/Alt-ExtUtils-PkgConfig-PLICEASE/workflows/linux/badge.svg)

Simplistic interface to pkgconf (like pkg-config)

# SYNOPSIS

```
env PERL_ALT_INSTALL=OVERWRITE cpanm Alt::ExtUtils::PkgConfig::PLICEASE
```

# DESCRIPTION

This distribution provides an alternative implementation of [ExtUtils::PkgConfig](https://metacpan.org/pod/ExtUtils::PkgConfig) which uses [PkgConfig::LibPkgConf](https://metacpan.org/pod/PkgConfig::LibPkgConf) 
(itself using `libpkgconf` which is the C library interface to `pkgconf`) instead of `pkg-config`.  It is unlikely
to replace the original module, but is intended to gather reliability statistics for [PkgConfig::LibPkgConf](https://metacpan.org/pod/PkgConfig::LibPkgConf) as compared
with the original version and `pkg-config`.

That being said, all effort has been made to make this module correct, and if you are in an environment where you have
`libpkgconf` but not `pkg-config`, then this module may be of use to you.  In order to get it to install you MUST set
the environment variable `PERL_ALT_INSTALL` to `OVERWRITE`.  For further rationale and details on this and other
"Alternative" implementation modules see [Alt](https://metacpan.org/pod/Alt).

Here are some differences between my version and the original:

- no forking

    Because this implementation uses a library instead of a program to query the `.pc` file database, this version does
    not need to use `fork` or `system`.

- no `AUTOLOAD`

    This version doesn't use `AUTOLOAD`.  As a result, dashed versions of the methods (`cflags-only-I`) are not supported.
    You must use the underscore methods (`cflags_only_I`).  As the dashed versions were probably unintentional that is
    probably okay.

# SEE ALSO

- [Alt](https://metacpan.org/pod/Alt)
- [ExtUtils::PkgConfig](https://metacpan.org/pod/ExtUtils::PkgConfig)
- [PkgConfig](https://metacpan.org/pod/PkgConfig)
- [PkgConfig::LibPkgConf](https://metacpan.org/pod/PkgConfig::LibPkgConf)

# AUTHOR

Graham Ollis <plicease@cpan.org>

# COPYRIGHT AND LICENSE

This software is Copyright (c) 2016 by Graham Ollis.

This is free software, licensed under:

```
The GNU Lesser General Public License, Version 2.1, February 1999
```
