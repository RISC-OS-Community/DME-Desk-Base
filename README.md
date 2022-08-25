# DME Desk Base

This repository hosts:

- DME !DeskCfg
- DME !DeskRes

All the components hosted in this repository are delivered using a single Packman RiscPkg package and therefore should always be built together.

This repository (together with DME-Core) are the base dependencies for all DME Suite components and extensions. 

> **Please note:** The reason for choosing short names is to ensure they are suitable for all RISC OS disk partitions/FileSystems.

## Status

This repository is still under initial development, so it's not ready yet for use.

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

## How to build this repository

You can either use GCC suite or ROOL DDE to build this repository.

To use GCC (or ROOL DDE) edit the `Config` file and ensure you comment out the lines for the suite you do NOT wish to use to build the repo.

Before you start your build, ensure that RISC OS Filer has seen the Compilers suite you would like to use to build this repo (otherwise the build process will fail return errors like "File not found" etc).

To start the build, double click on the `Mk` file from a RISC OS Filer window.

## FAQs

### Do I need the DeskCfg/DeskRes?

Yes, all my DME components expect them to be present. Please note, DME is being designed and built in components that cooperate with each-other, so you cannot just cherry pick one component and try to run it on its own.

### I have never heard of the license DME use now, do I need to worry?

No, CDDL v1.1 is actually a very friendly license for both commercial and fully OpenSource uses. There are few things that you must keep in mind if you want to modify any of the DME components, here some useful info for you:

[General info on the CDDL](https://www.mend.io/resources/blog/top-10-cddl-questions-answered/)

### Why CDDL?

This license was chosen to:

- Ensure everyone in the RISC OS community could benefit from the software
- Having a license that is compatible with RISC OS license
- Avoid people from taking the sources and not collaborating back their improvements (we want to ensure that the entire RISC OS community can always benefit from every improvement!)
- Have a commercial-software friendly license, so entities that want to produce commercial software can do so without legal issues, as long as they respect in full the CDDL license

### Why CDDL v1.1?

It includes some corrections that:

- Makes the CDDL compatible with European Copyright law
- Allow single developers to use the CDDL for their work

### Can I distribute DME components?

Yes, you can, but they rely on each-other, so we strongly recommend to download and use them via !Packman using the riscoscommunity.org official repository.

This not only installs everything correctly on your system and image, but also allow the end user to easily keep their system up-to-date.

If you have added/applied your own theming and customisations, do not worry, the update process does NOT change the customisations, nor removes them.

>**Please Note:** We only support standard installations, in other words installations done via !Packman using our repository. This is for obvious reasons, like we have no control and no idea on how non standard installation processes have been conducted, if all the file were installed correctly and if all the components "see" each-other etc. So, to open a support request here please ensure you have a standard installation of the entire DME ecosystem.

### How can I request for help in case of problems?

If you have a standard installation of the DME ecosystem, then please open a support ticket here on GitHub in the **Issues** section (link on the top menu).

### I have found and fixed some issues, how can I submit my changes back?

Please have a look at the [CONTRIBUTING](CONTRIBUTING.MB) guidelines for more details.

## Last note

Thanks for using RISC OS and the DME engine and all the components. If you want to submit ideas please feel free to use the Forum or open an Issue with your idea/suggestion.

Have fun! :)
