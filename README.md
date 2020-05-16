dodo
====
Desktop on [Digital Ocean](https://www.digitalocean.com/?refcode=92b0165840d8)


---


#### About
This script install a [MATE](https://mate-desktop.org/) desktop on the
[Debian Buster](https://www.debian.org/) droplet (Digital Ocean's cloud
computer) and you can use it via the web browser.

A team can share the desktop session at the same time. It's very suitable for
the collaboration or for the remote demonstration. It's also possible to run
different operating systems on the same session via
[VirtualBox](https://www.virtualbox.org/) too.

Thanks to [noVNC](https://github.com/novnc/noVNC),
[x11vnc](http://www.karlrunge.com/x11vnc/) and
[websockify](https://github.com/novnc/websockify)


---


#### Installation
Create a new Debian Buster (Debian 10) droplet and run the following commands
as `root`:

```bash
wget https://raw.githubusercontent.com/emrahcom/dodo/master/dodo
bash dodo
```


---


#### Screenshot
![dodo](dodo.png)


---


#### Let's Encrypt support
To use Let's Encrypt certificate, run the following commands:

```bash
FQDN="your.host.fqdn"

certbot certonly --webroot -w /var/www/html -d $FQDN

chmod 750 /etc/letsencrypt/{archive,live}
chown root:ssl-cert /etc/letsencrypt/{archive,live}
rm -f /etc/ssl/certs/ssl-eb.pem
rm -f /etc/ssl/private/ssl-eb.key
ln -s /etc/letsencrypt/live/$FQDN/fullchain.pem /etc/ssl/certs/ssl-eb.pem
ln -s /etc/letsencrypt/live/$FQDN/privkey.pem /etc/ssl/private/ssl-eb.key

systemctl restart websockify-secure.service
systemctl restart nginx.service
```

Try to connect using your FQDN. For example:

```
https://your.host.fqdn/novnc/?host=your.host.fqdn&port=6090&encrypt=1&password=YOUR-PASSWORD
```
