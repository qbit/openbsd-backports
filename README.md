openbsd-backports
==================================

Tree of OpenBSD ports that have been 'back ported' to work with the current stable
release of OpenBSD.

The main goal is to bridge the gap between ports and versions of ports that only
exist in the -current ports tree.

*OpenBSD OFFERS NO SUPPORT FOR THIS TREE, USE AT YOUR OWN RISK!*

How to use this tree
==================================

One way to use this tree is to clone it into your `/usr/ports/` directory and
adjust `PORTSDIR_PATH` accordingly in /etc/mk.conf:

	PORTSDIR_PATH=${PORTSDIR}:$(PORTSDIR)/openbsd-backports:${PORTSDIR}/mystuff

In the above example, a port with version 1 in cvs, version 2 in openbsd-backports.
Then, the version in cvs will be picked up before the version in openbsd-backports.
This is important if you are building packages using dpb. The order of
PORTSDIR_PATH is important.

To prevent "merge commits" from showing up in git log, it's recommended to
either update your tree with:

	git fetch && git rebase origin

or set the following option in `.git/config` in your local openbsd-backports repo
(see git-config(1) on `branch.<name>.rebase` and `branch.autosetuprebase`):

	git config branch.master.rebase true

Users of `py-hg-git` may update the tree issuing:

	hg pull --rebase


How to contribute
==================================

Please let me know if you need write access to this repository. But please
stick the workflow outlined in this document as well the pointers in
<https://openbsd.org/porting.html>
