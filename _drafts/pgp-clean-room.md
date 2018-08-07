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
Despite its problems, PGP is still used heavily by many open source
communities, especially [Debian](https://debian.org). Debian's web of trust is
the last line of defense between a Debian user and a malicious software update.
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

Links
-----

You'll probably want to read the [README](https://salsa.debian.org/tookmund-guest/make-pgp-clean-room/blob/master/README.md)
to understand how to build and use this project.

The latest builds can be found [here](http://pgpcr.tookmund.com/) or on [Google Drive](https://drive.google.com/open?id=12C4LbiZ8HuZFfPdZzRm561Wyg7TJiEvj)

Each build should come with a `.sig` file, signed by my
[GPG Key](/assets/3F90059E1AFDDD53.asc)

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

You can find links to all my weekly reports on the [project wiki page](https://wiki.debian.org/JacobAdams/PGPCleanRoomLiveCD)

Translators Wanted
------------------

The application has gettext support and [a partial German translation](https://salsa.debian.org/tookmund-guest/pgpcr/merge_requests/1),
but now that strings are final I would love to support more languages than
just English! See the [PGPCR README](https://salsa.debian.org/tookmund-guest/pgpcr/blob/master/README.md)
to get started, and thank you for your help!

Tasks yet to be accomplished
----------------------------
A look at the still [open issues](https://salsa.debian.org/tookmund-guest/pgpcr/issues)
shows that the project, while functionally complete, is not quite finished.

- [#16](https://salsa.debian.org/tookmund-guest/pgpcr/issues/16), lack of
randomness, is still a concern for generating keys.
[rngd](https://packages.debian.org/stretch/rng-tools5) fixes it for newer
hardware, but I'm still looking for ways to better present this problem to
the user. For now the application just freezes until the computer somehow
obtains enough entropy. If anyone knows how I could detect this state of low
entropy, please let me know, as I would love to at least inform the user of
what's happening.
- [#15](https://salsa.debian.org/tookmund-guest/pgpcr/issues/15), printing
the GPG master key and revocation certificate, would be nice but requires
both installing CUPS on the live CD and somehow configuring printing.
CUPS requires enough manual configuration right now that this seems
impossible as we can't know what PPDs are required. That's not even
considering that we could only support USB printers, as all networking is
intentionally disabled in the Clean Room Live CD.
- [#36](https://salsa.debian.org/tookmund-guest/pgpcr/issues/36), moving all
PKI operations to the [openssl](https://manpages.debian.org/stretch/openssl/openssl.1ssl.en.html)
command, would be nice but requires some studying of the incantations required.
For now the [pki](https://manpages.debian.org/stretch/strongswan-pki/pki.1.en.html)
command works and is significantly simpler to use. Had I another week I would
certainly do this but I'd like to set this project aside for a while and work
on other things.
- [#18](https://salsa.debian.org/tookmund-guest/pgpcr/issues/18) is
effectively solved by unconditionally calling `setupcon`, which we have to do
to setup non-standard keyboards anyway. However, this should be called by the
appropriate udev rules. Thus, I'm leaving the issue open until I figure out
what's going on.

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
