# DME Desk Base

This repository hosts:

- DME !DeskCfg
- DME !DeskRes

All the components hosted in this repository are delivered using a single Packman RiscPkg package and therefore should always be built together.

This repository (together with DME-Core) are the base dependencies for all DME Suite components and extensions. 

> **Please note:** The reason for choosing short names is to ensure they are suitable for all RISC OS disk partitions/FileSystems.

## !DeskCfg
This is the container for the configuration of all the components in the DME Suite.

It's directory structure is simple and DeskCfg is designed to work from RISC OS 3.00 up to latest RISC OS 5. It always offers the same access paths and behavior on all RISC OS release.

To access the configuration container simply use `DeskCfg:` path.

DeskCfg is also suitable to be provided via ShareFS, for example on those environment where one wants to configure a set of interconnected RISC OS devices with all identical configurations (for example classrooms or labs etc.)

When installed via PackMan, DeskCfg should get installed on your active `Choices` directory in your RISC OS Boot sequence.

If you are installing it manually, then we recommend to install it in your active `Choices` directory in your RISC OS Boot Sequence. However, if you need to share it live, across multiple RISC OS systems, then it's best to install it on your ShareFS shared directory and ensure that you configure DeskRes accordingly to search for DeskCfg in on your shared directory (more info on thi slater).

## !DeskRes
This is the container for all the components in the DME Suite.

DeskRes should be stored in !Boot.Resources and, not only it will host all the DME Suite components, but it will also enure that DeskCfg gets seen by the Filer before any of the DME components gets executed.

To access DeskRes structure from your own code you can use `DeskRes:` path.

When installed via PackMan, DeskRes will be installed in your RISC OS Boot Sequence (UniBoot) in `Resources` directory.

If you are installing it manually we recommend you to install it in your UniBoot in the `Resources` directory.

Even when using a distributed configuration (aka sharing DeskCfg via ShareFS) DeskRes should **always** be installed in your local UniBoot `Resources` on your RISC OS system. This also improve boot performance btw. 