# Services / Servers

The system would take care of setting up all needed servers. I'm not an expert here, so please take this as an alpha draft from someone with some idealistic ideas :)

All the server technology must not be visible to the end user at any time. This is something that would help to integrate Grand Decentral with existing clients like Mail applications, Address book apps or Calendars on mobile and desktop computers. The system should assist with those integrations as good as it can with providing well-written instructions for various setups or even step-by-step on-screen instructions. 

## Email

Sending and receiving emails should work out of the box. It needs an easy way to setup email addresses, inboxes and redirects. This should not be any more complicated than configuring email addresses on iOS. 

The email app comes with auto discovery for account settings in your client with automx.org (requires wildcard SSL certificate for subdomains). For security reasons, only encrypted connections are allowed. Optional, a function to easily create and manage GPG signatures for various mail accounts should be possible.

### Containers

- email-server
- email-storage
- email-webmail

## Calendar and Contacts

The calendar and contacs app consists of a simple CalDAV server, which also allows to expose the owner's contact details as a vCard.

### Containers

- caldav-server
- caldav-storage

## Avatar server

It allows to associate avatars to single mail addresses or whole domains, like Gravatar and exposes an API for avatar discoverability.

### Containers

- avatar-server
- avatar-storage

### Connects to

- Email app (discovery of hosted addresses)

## File server

Allows storing/sharing of files. Either via NFS/SMB in an internal network (showing up as network drives), SFTP on a web interface (like Dropbox or Owncloud). Ideally, files should be versioned/backed up automatically (e.g with something like Time Machine).

### Containers

- file-server
- file-storage
- file-webinterface

### Connects to

- Calendar and contacts (contacts for sharing files with)

## Web server

Meta container for offering to host own websites and applications. It contains sub-containers for installing web-applications like blogs, forums, analytics, etc.

## Communications

Chat services (based on XMPP) or video/screen sharing (via WebRTC)

### Containers

- communications-server

### Connects to

- Calendar and contacts (contacts for chatting)

## SSH server

This is a pretty important feature if the user is a tech expert and something breaks - but it should be available as a separate app, of course!

It should be as simple as possible and should only work with SSH key authentication - before being able to use the SSH login, the user would have to add his/her SSH public key to the web interface like GitHub.

There should be a shell providing all web interface features as a nice CLI.

This is rather optional and not required at the beginning, but would be a nice feature for power users.

## Discovery & uptime server

This is an optional (= the user will have to install it) application used to build a network between Grand Decentral Stations.  
The server itself works just like a DNS server: It builds an index of all known devices and syncs it from other discovery & uptime servers.

A new GDS can get into this network by communicating once with at least one other GDS (for example when sharing something).  
The other GDS (like *every* GDS even without a discovery & uptime server) has a list of some discovery & uptime servers (it will get to know them at the point when it communicates with them or when it gets pinged by one of them) and broadcasts the new information about the new GDS to some of them where the data is cached and can be retrieved by any GDS.

The data collected about each GDS would be:

- the URL pointing to the GDS
- a list of "mentoring servers" (see below)

This index is rebuilt every specific amount of time (for example every day) by pinging each GDS in the index.

The admin of the discovery & uptime server could define shorter intervals for specific domains of friends etc.  
If a GDS is down for more than a week or so, it gets removed from the index and the process starts from the beginning.

### Uptime server

A possible additional amazing feature made possible by this application is an uptime server notifying the admin of the GDS that his/her GDS is down.

That's where the "mentoring servers" come into play:  
If a user wants to enable the uptime monitoring functionality, he/she has to define a list of "mentoring servers" in the GDS administration panel. These are discovery & uptime servers hosted either by

- friends *or*
- dedicated fee-based monitoring services

These mentoring servers would keep an alternative email address (at another GDS/VPS/shared hosting/Gmail/Hotmail/whatever) to contact the admin of the GDS if it is down.

The process would be the following: When any discovery & uptime server finds out about a downtime of the GDS while rebuilding its index, it notifies a random different discovery & uptime server located at a different part of the world.

If the different server can reproduce that the GDS is down, this chain continues 5 times. If the server is up from any of these servers, the chain stops and everything goes back to normal.  
The fifth discovery & uptime server now pings one of the mentoring servers of the user (multiple if one is down) and tells it that the domain is down.

The mentoring server then checks again and if it can also reproduce this, it sends an email (or whatever communication channel the mentoring server implements) to the alternative email address of the admin.  
It then remembers that it sent that email and will refuse to send another one until the GDS was up in between.

The mentoring servers are needed to

- a) keep the email address secret to avoid spam
- b) prevent tons of emails by tons of discovery & uptime servers

### Motivation

Of course, the motivation to install a discovery & uptime server might not be that high as it consumes a lot of traffic and computing power.

A way to motivate people would be monetizing found downtimes by letting the admin of the tracked GDS define a budget for every email which would be divided among all involved servers.

This would probably lead to people modifying the software to claim that *every* GDS is down to save resources. The only way to fix this is a large number of discovery & uptime servers - some of them will still confirm that the server is up. This would stop the chain and the cheaters wouldn't have success.