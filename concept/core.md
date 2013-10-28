# Core

Base system, responsible for things like:

- General setup and global settings
- Managing applications
- Backup
- Security (e.g. SSL encryption)
- API
- Provides core services

GDS should also serve as an identification hub for Mozilla BrowserID based logins. When using docker.io as a basis, it's also possible to version control all changes made to the single containers, so it should be possible to return to a "last good" configuration, when things get messed up.

It's very important to keep it modular, though, so the initial download file is not that big.  
A possibility of implementing this would be a "Netinstall" image like the ones most Linux distributions offer only containing the real core and a really simple web interface guiding the user through the basic installation process.  
At the point when the user needs a specific feature (for example a specific database server or a specific programming language) which is not yet available, he will be asked to install it just like the "Java is not installed" alert in OS X.