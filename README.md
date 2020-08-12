# citrix

Re-installing my certificates
Re-reading the error message, I noticed that it was a specific certificate that was the problem.
Running a search, I was able to confirm that the said certificate is available from Entrust.

Once I’d downloaded the certificate in question, it was simply a matter of putting it where Citrix Receiver could see it.
So…

1
sudo cp entrust_g2_ca.cer /opt/Citrix/ICAClient/keystore/cacerts/.
Magically, Citrix Receiver was happy again and I was able to connect.

Some points to note for next time
A colleague of mine had the same issue. He is running Debian.
His solution was to :

– delete the files in the Citrix Receiver certs directory :

1
/opt/Citrix/ICAClient/keystore/cacerts/
– create a symlink in the directory from the certificates in

1
/etc/ssl/certs
If you’re reading this because you have a similar problem and the first solution doesn’t work, then perhaps this may be worth a try ( backup the certificate files before deleting them though !)
I’m still not sure of the root cause of this issue, although I suspect it may be something to do with browser updates.
On the plus side I’ve avoided having to drag myself into the office…for now.
