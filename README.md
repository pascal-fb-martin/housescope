# housescope
A manager for home servers.

This program runs as a Linux daemon and manage local home services:
- it runs background applications listed in its configuration.
- it automatically restarts an application if it detects that this application failed.
- it monitors the applications use of CPU and RAM, and the overall use of CPU and RAM on the server.
- it reports its status, and each application status, on a web service.
- it reports server and application metrics through a web service.

This program is designed to run as a sysV or systemd service. The reasons not to run the applications as direct systemd services are the following:
- systemd does not seem to restart any failed service. That is a problem for applications that sometime fail (motion).
- systemd does not seem to have a standard way to report status to a remote monitoring applications. one needs central monitoring when there is a significant number of small servers (e.g. Raspberry Pi, FriendlyElec's Nanopi Neo, etc.), whith each server implementing a single function (irrigation, security camera, file server, etc.).

The web access is not protected: this program only allows monitoring of the server. The program is designed to detects and automatically correct on its own any issue with any application it monitors.
