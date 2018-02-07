===============================
Reno stable branch merging test
===============================

This is a testcase to demonstrate some failings with how `reno`_ handles merges
from ``stable`` branches back into ``master``. The pattern used in most
OpenStack projects is to cherry-pick back, but this isn't always the case.

You can see the history by running::

    git log --all --graph

This will show the following steps:

#. Create an initial repo and make your initial release, version ``0.1.0``.

#. Add some release notes and make a **MAJOR** release, version ``1.0.0``.

#. Branch off from ``1.0.0`` to create ``stable/1.0``. Add some more release
   notes here and tag the commit as a **PATCH** release, version ``1.0.1``.

#. Add some more release notes to ``master``. Once done, merge in from
   ``stable/1.0`` to pull in the "fixes".

If you reset to ``HEAD~``, removing the merge commit added above, you will see
different release notes. Namely, thanks to the merge commits, any release notes
for the ``1.0.0`` release now appear under the section for release notes from
the ``master`` branch, rather than the ``stable/1.0`` branch as before.

This issue is tracked on `Launchpad`_.

.. _reno: https://pypi.python.org/pypi/reno
.. _Launchpad: https://bugs.launchpad.net/reno/+bug/1588309
