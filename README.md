# DME Desk Base
This repository hosts both:

* DME !DeskCfg
* DME !DeskRes

## !DeskCfg
This is the container for the configuration of all the components in the DME Suite.

It's directory structure is simple and DeskCfg is designed to work from RISC OS 3.00 up to latest RISC OS 5. It always offers the same access paths and behaviour on all RISC OS release.

To access the configuration container simply use:

```
DeskCfg:
```

Path.

DeskCfg is also suitable to be provided via ShareFS, for example on those environment where one wants to configure a set of interconnected RISC OS devices with all identical configurations (for example classrooms or labs etc.)

## !DeskRes
This is the container for all the components in the DME Suite.

DeskRes should be stored in !Boot.Resources and, not only it will host all the DME Suite components, but it will also enure that DeskCfg gets ssen by the Filer before any of the DME components gets executed.

