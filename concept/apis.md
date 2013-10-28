# APIs

## Discoverability API

Connect different GDS instances, e.g. for creating a decentralized social network or offer services to the community (e.g. "Hi, I'm server xyz and I offer these services …") It still needs to be solved, how the data for single users are handled in shared environments.

## Connecting instances
(just an idea)  
Let's assume Joe wants to connect his GDS instance with the one of Rick to gain access to Rick's files.  
An authentication process using a secret key could look like this:  
Joe puts the URL of Rick's GDS instace in a "Connect with an instance" dialog. Joe's GDS sents some kind of ping to Rick's GDS where a popup with a scerect connect-key shows up. Rick sends this connect-key to Joe e.g. via an ecrypted email. Joe now copies the connect-key into a dialog of his GDS instance.  
Now Joe's GDS instance hashes the connect-key and asks Rick's GDS instance if that hash equals the hash of the connect-key Rick's GDS just genrated for Joe's GDS instance.

## Administration API

Provide administration features of GDS to the outside. Possible tools connected to this would be:

- the web interface (client side code using the API)
- a command line interface installed right on the server (accessible using SSH) or on a remote workstation
- native remote applications (Windows, OS X, iOS, Android...) developed by third-party developers

This API would only work via HTTPS and would require authentication.