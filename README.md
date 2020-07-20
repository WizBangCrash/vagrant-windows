# Overview

This repository makes use of Stefan Scherer's Windows 10 vagrant box to build an
environment where I can run tests and use the communicator utilities, since
they have to have a Windows environment to run :-(

The box also supports testing out the PyPreConfig software.

Stafan updates the box regularly to be current with Microsoft's latest version
of Windows 10, so from time to time you will need to do a `vagrant box update`

## Basic Use

To use the box, just do a `vagrant up`. The VMWare UI will open up and you have
a Windows 10 box to use.

Wait for the VMWare tools to install and follow the onscreen instructions.
**NOTE** Until the VMWare Tool are installed the mouse pointer may be offset

The User:Password is vagrant:vagrant

## Test PyPreconfig

To use the box to test PyPreConfig first run the following provisioners:

```shell
  vagrant provision --provision-with vcredist-all,python354,vscode
```

Then goto the box and open a powershell window where you can run the following:

```shell
> cd /vagrant/DemoPack/PyPreConfig
> pip install PreConfig-<vers>
> pip install pywin32
> cd Test
```

Then edit the Configuration.xlsx spreadsheet with whatever setup you want to test.

Follow preconfig instructions on how to set up the files and what tests to run.