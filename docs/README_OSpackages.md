This script installs base OS RPMs into chroot-dev target-disk (previously configured by the `DiskSetup.sh` and mounted by the `MkChrootTree.sh` scripts)

~~~
./OSpackages.sh [GNU long option] [option] ...
Usage: ./OSpackages.sh [GNU long option] [option] ...
  Options:
        -a  List of repository-names to activate
              Default activation: BaseOS,AppStream,extras
        -g  RPM-group to intall (default: "core")
        -h  Print this message
        -m  Where to mount chroot-dev (default: "/mnt/ec2-root")
        -M  File containing list of RPMs to install
        -r  List of repo-def repository RPMs or RPM-URLs to install
        --help              See "-h" short-option
        --mountpoint        See "-m" short-option
        --pkg-manifest      See "-M" short-option
        --rpm-group         See "-g" short-option
        --repo-activation   See "-a" short-option
        --repo-rpms         See "-r" short-option
~~~

Each of the functionality flag-options may also be specified by using environment variables:

- `CHROOTMNT`: Stands in for the `-m`/`--mountpoint` flag-option. This env (or corresponding flags) is only necessary if the corresponding flag was used to override the `MkChrootTree.sh` script's default behavior.
- `OSREPOS`: Stands in for the `-a`/`--repo-activation` flag-option. Primarily for use with private repositories. Specify a comma-delimted list of logical repository-names to activate.
- `REPORPMS`:Stands in for the `-r`/`--repo-rpms` flag-option. Primarily for use with private repositories. Specify a comma-delimted list of repository-definition RPMs (or URLs to same) to install.
- `RPMFILE`: Stands in for the `-M`/`--pkg-manifest` flag-option. Primarily used for highly-customized builds or with private repositories that don't have standard RPM-group metadata available. Not yet implemented or tested.
- `RPMGRP`: Stands in for the `-g`/`--rpm-group` flag-option. Primarily used when trying to build non-"Core" AMIs (only minimally tesed).

Further, additional output/logging can be generated by setting the `DEBUG` environment variable to "`true`". Doing so causes information that is normally only directed to syslog to also be printed to `STDOUT`.

## Notes:

<sup>1</sup>If invoking scripts interactively, the `DEBUG` value is automatically set to true.

