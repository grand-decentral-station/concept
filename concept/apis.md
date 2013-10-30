# APIs

## Discoverability API

Connect different GDS instances, e.g. for creating a decentralized social network or offer services to the community (e.g. "Hi, I'm server xyz and I offer these services …") It still needs to be solved, how the data for single users are handled in shared environments.

## Connecting instances

There are multiple ways described in [Issue #20](https://github.com/grand-decentral-station/concept/issues/20):

- Using secret keys

	1. Joe wants to connect his GDS instance with the one of Rick to gain access to Rick's files.  
	2. Joe puts the URL of Rick's GDS instance in a "Connect with an instance" dialog.
	3. Joe's GDS sends some kind of ping to Rick's GDS where a popup with a secret connect-key shows up.
	4. Rick sends this connect-key to Joe e.g. via an encrypted email.
	5. Joe now copies the connect-key into a dialog of his GDS instance.  
	6. Joe's GDS instance hashes the connect-key and asks Rick's GDS instance if that hash equals the hash of the connect-key Rick's GDS just generated for Joe's GDS instance.

- Using invitation

	1. Rick wants to share some of his photos with Joe
	2. Rick adds the user id of Joe (`joe@domainofhisgds.tld`) to the list of people with access and can give him write or only read privileges.
	3. Rick's GDS pings the GDS of Joe at the domain domainofhisgds.tld
  		- If there is a GDS living under the domain domainofhisgds.tld, Joe gets a message telling him he has access and can then see the content from Rick's GDS just like it would be stored on his own one
  		- If there is **no** GDS living there (= normal email address), Joe gets an email telling him that he can now interact with Rick's data using a secret (and long) share URL pointing right to Rick's GDS
	4. Done

- Using connection requests

	1. Joe arrives at Rick's social profile / website / service and wishes to connect
	2. Joe pushes the 'connect' button. As a pre-authenticated GDS user (joe@domainofhisgds.tld), a connect request is sent automatically to Rick.
	3. Via email or web interface, Rick can accept or deny Joe's request.
	4. Done

	To avoid spam, GDS could limit people able to request access to "friends of friends" like in the Facebook "discoverability" options. Alternatively, it could be switched to "invite only".


## Administration API

Provide administration features of GDS to the outside. Possible tools connected to this would be:

- the web interface (client side code using the API)
- a command line interface installed right on the server (accessible using SSH) or on a remote workstation
- native remote applications (Windows, OS X, iOS, Android...) developed by third-party developers

This API would only work via HTTPS and would require authentication.

## Settings API

An API for applications to announce settings for the administration API.  
An application could first provide GDC with information about what settings exist, what valid values they can have and with descriptions in different languages using the settings API.

These would then be exposed to the outside using the administration API so the user can actually change the settings commonly for all applications without needing to use tons of different tools for that.

GDC remembers the current settings of each application and provides them back to the application using API endpoints of the settings API whenever the application needs them.

It has yet to be decided which field types are required to represent every possible setting (most likely quite a lot!).