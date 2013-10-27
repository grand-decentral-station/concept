# Core

Base system, responsible for things like:

- General setup and global settings
- Managing applications
- Backup
- Security (e.g. SSL encryption)
- API
- Provides core services

GDS should also serve as an identification hub for Mozilla BrowserID based logins. When using docker.io as a basis, it's also possible to version control all changes made to the single containers, so it should be possible to return to a "last good" configuration, when things get messed up.