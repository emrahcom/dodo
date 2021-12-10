## dodo

Desktop on the cloud

#### About

This installer creates a [MATE](https://mate-desktop.org/) desktop on the
[Debian Bullseye](https://www.debian.org/) cloud machine and you can use it via
the web browser.

A team can share this desktop environment at the same time. It's very suitable
for the collaboration or for the remote demonstration. It's also possible to run
different operating systems on the same session via
[virt-manager](https://virt-manager.org/) or
[VirtualBox](https://www.virtualbox.org/) too.

Thanks to [noVNC](https://github.com/novnc/noVNC),
[x11vnc](http://www.karlrunge.com/x11vnc/) and
[websockify](https://github.com/novnc/websockify)

#### Installation

Create a new Debian 11 Bullseye cloud machine and run the following commands as
`root`:

```bash
wget -O dodo-bullseye-installer https://raw.githubusercontent.com/emrahcom/dodo/master/dodo-bullseye-installer
bash dodo-bullseye-installer
```

#### Screenshot

![dodo](dodo.png)

#### Let's Encrypt support

Run the following commands to add Let's Encrypt certificate:

```bash
set-letsencrypt-cert "your.host.fqdn"

systemctl restart websockify-secure.service
systemctl restart nginx.service
```

Try to connect using your FQDN. For example:

```
https://your.host.fqdn/novnc/?host=your.host.fqdn&port=6090&encrypt=1&resize=scale&password=YOUR-PASSWORD
```
