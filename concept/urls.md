# URLs

This document is intended as an overview of all URL schemes used in GDS.


## Station domain

All stations in GDS have a unique generic domain used for identification. The
station domain helps to organize the decentralization aspect of GDS. This way a
user can order GDS to move all of his data from one machine/provider to another.

```
vs12.lukeskywalker.de
home.lukeskywalker.de
```


## User domain

All users in GDS have there own custom domain as a entry point. In order not to
conflict with existing infrastructure, GDS is supposed to be used on a
subdomain. This way for example a user with a pre-existing homepage can add GDS
without problems and it allows for two scenarios.


### Single User Domain

The user has it's own top level domain for GD.

```
gd.lukeskywalker.com
```


### Multi User Domain

Multiple users share one top level domain for GDS.

```
luke.provider.com
leia.provider.com
han.provider.com
```


## Path structure

After the domain all GD modules/carriages and its core are encoded in paths.
If have a mail applications installed all its functionality would be acceptable
under ```gds.lukeskywalker.com/mail/<*>```.

```
gds.lukeskywalker.com/<path>
```
