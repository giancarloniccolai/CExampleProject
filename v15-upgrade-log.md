# Upgrade log for SpatialOS 15.0.0

This log provides the list of changes made to this project to upgrade it from
SpatialOS 14.9.0 to SpatialOS 15.0.0. You can follow a similar sequence of steps
to upgrade your project.

We will first migrate away from any deprecated functionality that we can on
14.9.0. This step very much depends on what functionality a project uses, and
whether or not you have already made similar changes when APIs got deprecated.

1. Use the new logging API instead of `LogMessageOp`s. For simplicity, we log
   all messages with log-level Warning and above, and Info messages related to
   establishing the connection.

Now we will upgrade to SpatialOS 15.0.0.

1. Update the version numbers used in `spatialos.json`.
1. Remove unsupported bridge settings from all `worker.json`s. The settings
   were used for legacy load balancing and interest systems. Both of these
   systems have been re-worked and replaced, and these options are no longer
   relevant.
1. Update which worker packages are used by the project. Debug packages are no
   longer available by default, and Linux packages have been renamed to reflect
   compiler upgrades. Refer to the full release notes to see how this changed
   the runtime requirements. For example, the required minimum version of
   `glibc` has increased on Linux, which might cause incompatibility with old
   Linux distributions.
1. Update the build scripts to address the lack of availability of Windows debug
   packages, and the removal of the raknet static library.