# APIs

## Discoverability API

Connect different GDS instances, e.g. for creating a decentralized social network or offer services to the community (e.g. "Hi, I'm server xyz and I offer these services …") It still needs to be solved, how the data for single users are handled in shared environments.

## Administration API

Provide administration features of GDS to the outside. Possible tools connected to this would be:

- the web interface (client side code using the API)
- a command line interface installed right on the server (accessible using SSH) or on a remote workstation
- native remote applications (Windows, OS X, iOS, Android...) developed by third-party developers

This API would only work via HTTPS and would require authentication.