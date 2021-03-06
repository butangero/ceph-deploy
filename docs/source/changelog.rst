1.3
---
* Major refactoring for all the remote connections in ceph-deploy. With global
  and granular timeouts.
* Raise the log level for missing keyrings
* Allow ``--username`` to be used for connecting over SSH
* Increase verbosity when MDS fails, include the exit code
* Do not remove ``/etc/ceph``, just the contents
* Use ``rcceph`` instead of service for SUSE
* Fix lack of ``--cluster`` usage on monitor error checks
* ensure we correctly detect Debian releases

1.2.7
-----
* Ensure local calls to ceph-deploy do not attempt to ssh.
* ``mon create-initial`` command to deploy all defined mons, wait for them to
  form quorum and finally to gatherkeys.
* Improve help menu for mon commands.
* Add ``--fs-type`` option to ``disk`` and ``osd`` commands (Thanks Benoit
  Knecht)
* Make sure we are using ``--cluster`` for remote configs when starting ceph
* Fix broken ``mon destroy`` calls using the new hostname resolution helper
* Add a helper to catch common monitor errors (reporting the status of a mon)
* Normalize all configuration options in ceph-deploy (Thanks Andrew Woodward)
* Use a ``cuttlefish`` compatible ``mon_status`` command
* Make ``osd activate`` use the new remote connection libraries for improved
  readability.
* Make ``disk zap`` also use the new remote connection libraries.
* Handle any connection errors that may came up when attempting to get into
  remote hosts.

1.2.6
-----
* Fixes a problem witha closed connection for Debian distros when creating
  a mon.

1.2.5
-----
* Fix yet another hanging problem when starting monitors. Closing the
  connection now before we even start them.

1.2.4
-----
* Improve ``osd help`` menu with path information
* Really discourage the use of ``ceph-deploy new [IP]``
* Fix hanging remote requests
* Add ``mon status`` output when creating monitors
* Fix Debian install issue (wrong parameter order) (Thanks Sayid Munawar)
* ``osd`` commands will be more verbose when deploying them
* Issue a warning when provided hosts do not match ``hostname -s`` remotely
* Create two flags for altering/not-altering source repos at install time:
  ``--adjust-repos`` and ``--no-adjust-repos``
* Do not do any ``sudo`` commands if user is root
* Use ``mon status`` for every ``mon`` deployment and detect problems with
  monitors.
* Allow to specify ``host:fqdn/ip`` for all mon commands (Thanks Dmitry
  Borodaenko)
* Be consistent for hostname detection (Thanks Dmitry Borodaenko)
* Fix hanging problem on remote hosts

1.2.3
-----
* Fix non-working ``disk list``
* ``check_call`` utility fixes ``$PATH`` issues.
* Use proper exit codes from the ``main()`` CLI function
* Do not error when attempting to add the EPEL repos.
* Do not complain when using IP:HOST pairs
* Report nicely when ``HOST:DISK`` is not used when zapping.

1.2.2
-----
* Do not force usage of lsb_release, fallback to
  ``platform.linux_distribution()``
* Ease installation in CentOS/Scientific by adding the EPEL repo
  before attempting to install Ceph.
* Graceful handling of pushy connection issues due to host
  address resolution
* Honor the usage of ``--cluster`` when calling osd prepare.

1.2.1
-----
* Print the help when no arguments are passed
* Add a ``--version`` flag
* Show the version in the help menu
* Catch ``DeployError`` exceptions nicely with the logger
* Fix blocked command when calling ``mon create``
* default to ``dumpling`` for installs
* halt execution on remote exceptions


1.2
---
* Better logging output
* Remote logging for individual actions for ``install`` and ``mon create``
* Install ``ca-certificates`` on all Debian-based distros
* Honor the usage of ``--cluster``
* Do not ``rm -rf`` monitor logs when destroying
* Error out when ``ceph-deploy new [IP]`` is used
* Log the ceph version when installing
