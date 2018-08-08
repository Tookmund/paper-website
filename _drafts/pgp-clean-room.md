---
layout: post
title: "PGP Clean Room 1.0 Release"
description: "As GSoC 2018 comes to a close, the PGP Clean Room reaches a stable release."
category: 
tags: [debian]
---

After several months of work, I am proud to announce that my GSoC 2018 project,
the PGP/PKI Clean Room, has arrived at a stable (1.0) release!

PGP/PKI Clean Room
------------------
PGP is still used heavily by many open source communities, especially
[Debian](https://debian.org). Debian's web of trust is the last line of
defense between a Debian user and a malicious software update.
Given the availability of GPG subkeys, the safest thing would be to store one's
private GPG master key offline and use subkeys regularly. However, many do not
do this as it can be a complex and arcane process.

The PGP Clean Room aims to simplify this by allowing a user to safely create
and store their master key offline while exporting their subkeys, either to
a USB drive for importing on thier computer, or to a smartcard, where they can
be safely used without ever directly exposing one's private keys to an
Internet-connected computer.

The PGP Clean Room also supports PKI, allowing one to create a Certificate
Authority and issue certificates from Certificate Signing Requests.

Translators Wanted
------------------

The application has gettext support and [a partial German translation](https://salsa.debian.org/tookmund-guest/pgpcr/merge_requests/1),
but now that strings are final I would love to support more languages than
just English! See the [PGPCR README](https://salsa.debian.org/tookmund-guest/pgpcr/blob/master/README.md)
to get started, and thank you for your help!

Links
-----

You'll probably want to read the [README](https://salsa.debian.org/tookmund-guest/make-pgp-clean-room/blob/master/README.md)
to understand how to build and use this project.

The latest builds can be found [here](http://pgpcr.tookmund.com/) or on [Google Drive](https://drive.google.com/open?id=12C4LbiZ8HuZFfPdZzRm561Wyg7TJiEvj).

Each build should come with a `.sig` file, signed by my
[GPG Key](/assets/3F90059E1AFDDD53.asc).

[pgpcr](https://salsa.debian.org/tookmund-guest/pgpcr): This repository
contains the source code of the PGP Clean Room application.
It allows one to manage PGP and PKI/CA keys, and export PGP subkeys for
day-to-day usage.

[make-pgp-clean-room](https://salsa.debian.org/tookmund-guest/make-pgp-clean-room):
This repository holds all of the configuration required to build a live CD
for the PGP Clean Room application. This is the recommended way to run the
application and allows for easy offline key pair management.
Everything from commit [a50e2aae](https://salsa.debian.org/tookmund-guest/make-pgp-clean-room/commit/a50e2aae93b855dcacabffa8320369941e1855a5)
forward was part of GSoC 2018.

The project changelog, which was a day-by-day log of my activities, can be
found [here](https://salsa.debian.org/tookmund-guest/pgpcr/blob/master/CHANGELOG.md).

You can find links to all my weekly reports on the
[project wiki page](https://wiki.debian.org/JacobAdams/PGPCleanRoomLiveCD).

Bugs Filed
----------
Over the course of this project I also filed a few bugs with other projects.
- [Debian #903681](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=903681),
about psf-unifont's unneeded dependency on bdf2psf.
- [GNUPG T4001](https://dev.gnupg.org/T4001), about exposing import and export
functions in the GPGME python bindings.
- [GNUPG T4052](https://dev.gnupg.org/T4052), about GPG's inability to guess
an algorithm for P-curve signing and authentication keys.

Screenshots
-----------
![Main Menu](/assets/pgpcr/1.0-mainmenu.png)

![Generating GPG Key](/assets/pgpcr/1.0-gpggen.png)

![Progress Bar](/assets/pgpcr/1.0-progress.png)

![Generating GPG Signing Subkey](/assets/pgpcr/1.0-subkey.png)

![GPG Key Backup](/assets/pgpcr/1.0-backup.png)

![Setting up a Smartcard](/assets/pgpcr/1.0-smartcard.png)

![Loading a GPG Key from a Backup](/assets/pgpcr/1.0-loadkey.png)

![CA Creation](/assets/pgpcr/1.0-CA.png)

![Advanced Menu](/assets/pgpcr/1.0-adv.png)
