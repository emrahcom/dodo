How to connect to Dodo server
=============================

Replace the "___HOST___" value with your host address.

Unsecure link (no certificate):
  http://___HOST___/novnc/?host=___HOST___&port=6080&encrypt=0&resize=scale&password=___PASSWD___

Secure link (self-signed, needed to import the CA certificate):
  https://___HOST___/novnc/?host=___HOST___&port=6090&encrypt=1&resize=scale&password=___PASSWD___

The self-signed CA certificate (add this as a trusted CA certificate):
  http://___HOST___/dodo-ca.pem

Default VNC Password: ___PASSWD___

To change password (as dodo user): 
  su -l dodo
  x11vnc -storepasswd /home/dodo/.vnc/passwd
