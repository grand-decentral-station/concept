# Applications

## Installation & updates

They system would take care of installing apps and keeping them up to date regularly. The system would also update itself. It might be something to think about to offer auto-updates/forced-updates for critical security updates, so that servers are running on the most secure and stable version all the time. 

The system would install each app in a sandboxed environment. Docker.io could be a great basis for this. Each app can interact with other apps through APIs and for various interactions it would need the admission from the user. So malware wouldn't be able to destroy or access other parts of the system except content within the sandbox. 

The installation process should be a simple one-click process compared to the installation of applications on Android or iOS. Payments should be handled smoothly (see Payment integration)

Removing apps should be as simple as installing them.

## Packaging

All files for an app would be wrapped in a zip file. A app.json file would contain all the necessary information about the app that would be available for the system. 

A possible app.json could look similar to this: 

```json
{
    "name": "Birdy",
    "description": "A decentralized alternative to Twitter",
    "version": "1.0",
    "author": "MacGyver",
    "url": "http://getbirdyapp.com",
    "source" : "http://getbirdyapp.com/source.zip",
    "icon" : "assets/images/birdy-icon.svg",
    "screenshots" : "assets/screenshots",
    "price" : "$4.99"
}
```

### Containers / Sandboxes

Each GDS application is a "meta-container" with one or more containers which make up the application. Each app has a separate storage container, where all data is saved separately from the application. So you can switch – for example – the mail server component while your data stays untouched. This also helps with backups.

All apps run completely sandboxed and communicates over a simple JSON api with the GDS core (e.g. service name/type, URLs/ports for service endpoints, meta info, etc.)

## App Store

It should be decentralized as well, so there could be an "app server" app for GDC to host your own app repository. A user could then subscribe to that server using its URL and could browse, buy and download apps directly from there.