# Applications

## Installation & updates

They system would take care of installing apps and keeping them up to date regularly. The system would also update itself. It might be something to think about to offer auto-updates/forced-updates for critical security updates, so that servers are running on the most secure and stable version all the time. 

The system would install each app in a sandboxed environment. Docker.io could be a great basis for this. Each app can interact with other apps through APIs and for various interactions it would need the admission from the user. So malware wouldn't be able to destroy or access other parts of the system except content within the sandbox. 

Payments should be handled smoothly (see Payment integration)

The installation process would be handled via git. By installing an app the installer mirrors the repository and analyzes its content, afterwards it installs the analyzed dependencies in a clean new environment, runs the test suite and sets up database connections, GDS api permissions etc. similar to other PaaS providers like Heroku.
If wished the appstore could check every day for new tags and install the updates. All this would be handled behind a great UI with a simple one-click install process, the User would never be confronted with git or other technical terms.

Removing apps would mean deleting the mirrored git repository, the used databases and other data storages. All triggered by a simple click on the Remove App button.
Just Works.™

## Platform

That being said, it's important to keep in mind, that the GDS is not a developers private PaaS playground. Most people will not run their GDS on the latest hardware, so resources should be used carefully.
Therefore the GDS should provide an already installed stack to develop applications.
This provided stack could follow a no-backend philosophy like Hood.ie. 
By doing so front-end developers would be elated to develop apps without knowing everything about databases, caching, email server implementation, etc. 

Of course there are apps that don't fit well into a no-backend philosophy because of their dependencies or complexity. These apps could still use their own self chosen stack. The GDS platform should not force anybody to develop in a specific language or framework, but encourage the use of the provided infrastructure.

## Packaging

All files for an app would be wrapped in a git repository. A app.json file would contain all the necessary information about the app that would be available for the system.

A possible app.json could look similar to this: 

```json
{
    "name": "Birdy",
    "description": "A decentralized alternative to Twitter",
    "version": "1.0",
    "author": "MacGyver",
    "url": "http://getbirdyapp.com",
		"repository": "https://mygit.com/MacGyver/birdapp.git",
    "icon" : "assets/images/birdy-icon.svg",
    "screenshots" : "assets/screenshots",
    "price" : "$4.99"
}
```


### Containers / Sandboxes

Each GDS application is a "meta-container" with one or more containers which make up the application. Each app has a separate storage container, where all data is saved separately from the application. So you can switch – for example – the mail server component while your data stays untouched. This also helps with backups.

All apps run completely sandboxed and communicate over a simple JSON api with the GDS core (e.g. service name/type, URLs/ports for service endpoints, meta info, etc.)

There are several problems with this described in [Issue #5](https://github.com/grand-decentral-station/concept/issues/5) and [Issue #23](https://github.com/grand-decentral-station/concept/issues/23) which have yet to be solved.

## App Store

It should be decentralized as well, so there could be an "app server" app for GDC to host your own app repository. A user could then subscribe to that server using its URL and could browse, buy and download apps directly from there.

## Intents

There should be an Android-like intent system where any application can provide e.g. "calendar", "file-sync", "addressbook" and so on. The intent has a protocol that must be implemented which is specific to the various intents. 3rd party intents can also be provided, perhaps through some kind of central register over intents and their purposes.

This is much more flexible than having a calendar app build in to the system itself. It's more flexible for the developers since we don't have to rely on a specific implementation of a calendar. And it's more flexible for the user, they can chose their own calendar app, instead of being forced to use the one that's built-in.
