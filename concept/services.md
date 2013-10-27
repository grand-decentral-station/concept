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

