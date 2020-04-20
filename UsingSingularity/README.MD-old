# Using Singularity

<span class="twiki-macro TOC"></span>
<span class="twiki-macro STARTINCLUDE"></span>

# Introduction

## What are Containers?

**Containers** are an operating system virtualization technology used to
package applications and their dependencies and run them in isolated
environments. Unlike Virtual Machines, they share the host OS kernel,
thus provide a **lightweight** method of packaging and deploying
applications in a standardized way across many different types of
infrastructure.

## What is Singularity?

\* [Singularity](https://sylabs.io/)\* is a container platform. It
allows you to create and run containers that package up pieces of
software in a portable and reproducible way. In contrast to
[Docker](https://docs.docker.com/), Singularity does not give superuser
privileges. And it can access to the GPU on a host node in native speed.

You can build a container using Singularity on your laptop, and then run
it on the grid. You can also make use of many already existing container
images from different sources.

# Installation of Singularity

## Singularity on Linux OS

Most Linux Distros should come with the Singularity. For example,
Singularity is already available on **lxplus** machines at CERN.

    lxplus$ singularity --version
    singularity version 3.5.3-1.1.el7

If it does not come with your Linux OS, you can find the installation
instruction for the version of 3.5 (the latest one currently):

<https://sylabs.io/guides/3.5/admin-guide/installation.html>

The singularity maintained in Linux distribution repos (via apt or yum)
tends to be older. If you like to install the latest version, you can
visit [the gitlab source
site](https://github.com/sylabs/singularity/releases) to install from
the source.

## Singularity on Mac OS

Since Mac OS does not use Linux kernel, the Singularity for Linux does
not work here. However, a new Singularity Desktop for Mac OS has been
developed to take Linux-based containers. The installation instruction
can be found [here](https://sylabs.io/singularity-desktop-macos/). It is
still a beta release, and distributed as a DMG file (Mac OS disk image).
The current beta release version is:

    MacOS$ singularity --version
    singularity version 3.3.0-rc.1.658.g7427b73f1.dirty

As stated on the page of [Singularity Desktop
MacOS](https://sylabs.io/singularity-desktop-macos/), there are some
limitations.

Run **singularity -h** to find the full available commands and options.
In comparison with the Singularity-3.5 on Linux, the Singularity on Mac
OS misses many commands such as **inspect** and **instance**.

## Singularity on Windows 10

In order to use Singularity on Windows, you need install a Linux distro
first. It could be achieved through [Windows Subsystem for Linux
(WSL)](https://docs.microsoft.com/en-us/windows/wsl/faq) without
involving a Virtual Machine. **WSL** is a new Windows 10 feature that
enables you to run native Linux command-line tools directly on Windows.
So it is not available for other old Windows such as Windows 7.

### Installation of Windows Subsystem for Linux (WSL)

Please refer [the WSL installation guide for
Windows 10](https://docs.microsoft.com/en-us/windows/wsl/install-win10).

First enable the option feature **Microsoft-Windows-Subsystem-Linux**.
Open **PowerShell as Administrator** and run:

    Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux

When prompted restart the computer.

Then you can install your preferred Linux Distro, following [the link on
the Microsoft
store](https://docs.microsoft.com/en-us/windows/wsl/install-win10),
where there is no CentOS available. However, you can find the
installation guide for CentOS at
[TipsMake.com](https://tipsmake.com/install-centos-on-windows-10-wsl).
Or download directly [the zip file at
github](https://github.com/yuk7/CentWSL) and following the instruction
to install it.

Once your distro has been downloaded and installed, you will be prompted
to **create a new user account** together with its password to
[initialize the new Linux
distro](https://docs.microsoft.com/en-us/windows/wsl/initialize-distro).

### Running Windows 10 build 18917 or higher

In order to install WSL2, ensure that you are running Windows 10 **build
18917** or higher. You can check your Windows version by opening
**Command Prompt** and running the **ver** command.

> Microsoft Windows \[Version 10.0.19587.1000\] (c) 2020
> Microsoft Corporation. All rights reserved.
> 
> C:\\Users\\Shuwei\>ver
> 
> Microsoft Windows \[Version 10.0.19587.1000\]

Actually the Windows build information has already be displayed on the
terminal top when the **Command Prompt** app is opened.

You can also check the Windows build info in PowerShell with command
**systeminfo**:

> PS C:\\Users\\Shuwei\> systeminfo | Select-String "^OS
> Name","^OS Version"
> 
> OS Name: Microsoft Windows 10 Home Insider Preview OS Version:
> 10.0.19587 N/A Build 19587

If your Windows build is lower than **18917**, you can update it by
joining the Windows Insider Program and select the **Fast ring** or the
**Slow ring**. Search for `"Windows Insider Program"` in the Windows
start search box, and click the found **Windows Insider Program
settings**. In the setting, pick your Insider settings to **Fast** or
**Slow** ring. You can find more details at [How to get started with
Windows 10 Insider Preview
builds](https://insider.windows.com/en-us/getting-started/#install).

### Installation of WSL2

You can find [the detailed instruction on installing WSL2 on
Windows 10](https://docs.microsoft.com/en-us/windows/wsl/wsl2-install).
The first 2 requirements have already been discussed above. Next you
need:

  - Enable the 'Virtual Machine Platform' optional component
  - Set a distro to be backed by WSL2 using the command line
  - Verify what versions of WSL your distros are using

To Enable the **Virtual Machine Platform**, run **PowerShell as
Adminstrator** with:

    dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
    dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart

Then restart the computer.

Next set the Linux dsitro to WSL2 by the following command under
**PowerShell**: \<pre\> wsl --set-default-version 2 \</pre\> which may
take a while to apply.

Now you can verify which WSL version used the Linux distro.

> PS C:\\Users\\Shuwei\> wsl -l -v NAME STATE VERSION \*
> Ubuntu-18.04 Stopped 2

### Use the Installed Linux on Windows 10

Open **PowerShell under a regular user** and run **wsl**:

> PS C:\\Users\\Shuwei\> wsl
> <yesw2000@Home-Dell660>:/mnt/c/Users/Shuwei$ echo $0 -bash
> <yesw2000@Home-Dell660>:/mnt/c/Users/Shuwei$

which starts the Linux and enter **bash**.

You can also start the Linux by searching **wsl** or **bash** on the
Windows Start Search Box and click on **wsl Run command** or **bash Run
command**.

If the Linux is already running, you can run "bash" to enter the Linux:

> PS C:\\Users\\Shuwei\> wsl -l -v NAME STATE VERSION \*
> Ubuntu-18.04 Running 2 PS C:\\Users\\Shuwei\> bash
> <yesw2000@Home-Dell660>:/mnt/c/Users/Shuwei$ 

After all terminals associated with the Linux have been closed, the
running Linux will stop then.

### Singularity Installation on WSL2

Start the Linux distro on Windows, then install Singularity as the same
ways as on the Linux OS.

# Using Singularity

## Singularity Usage Help

You can find the Singularity usage by running **singularity -h**

    lxplus$ singularity -h
    
    Linux container platform optimized for High Performance Computing
    (HPC) and Enterprise Performance Computing (EPC)
    
    Usage:
      singularity \[global options...\]
    
    Description:
      Singularity containers provide an application virtualization layer enabling
      mobility of compute via both application and environment portability. With
      Singularity one is capable of building a root file system that runs on any 
      other Linux system where Singularity is installed.
    
    Options:
      -d, --debug     print debugging information (highest verbosity)
      -h, --help      help for singularity
          --nocolor   print without color output (default False)
      -q, --quiet     suppress normal output
      -s, --silent    only print errors
      -v, --verbose   print additional information
          --version   version for singularity
    
    Available Commands:
      build       Build a Singularity image
      cache       Manage the local cache
      capability  Manage Linux capabilities for users and groups
      config      Manage various singularity configuration (root user only)
      delete      Deletes requested image from the library
      exec        Run a command within a container
      help        Help about any command
      inspect     Show metadata for an image
      instance    Manage containers running as services
      key         Manage OpenPGP keys
      oci         Manage OCI containers
      plugin      Manage Singularity plugins
      pull        Pull an image from a URI
      push        Upload image to the provided URI
      remote      Manage singularity remote endpoints
      run         Run the user-defined default command within a container
      run-help    Show the user-defined help for an image
      search      Search a Container Library for images
      shell       Run a shell within a container
      sif         siftool is a program for Singularity Image Format (SIF) file manipulation
      sign        Attach a cryptographic signature to an image
      test        Run the user-defined tests within a container
      verify      Verify cryptographic signatures attached to an image
      version     Show the version for Singularity
  
    Examples:
      $ singularity help <command> [<subcommand>]
      $ singularity help build
      $ singularity help instance start

The most frequently used commands are: **run**, **exec**, **shell** and
**pull**.

For additional help or support, please visit
<https://www.sylabs.io/docs/>. For quick start of version-3.5, you can
refer to [the User
Guide](https://sylabs.io/guides/3.5/user-guide/quick_start.html#).

## Cache Folders

To make downloading images for build and pull faster and less redundant,
Singularity uses a caching strategy. By default, Singularity will create
a set of **cache folders** in your **$HOME** directory for docker
layers, Cloud library images, and metadata, respectively:

  - $HOME/.singularity/cache/library
  - $HOME/.singularity/cache/oci
  - $HOME/.singularity/cache/oci-tmp

which could take quite much space, depending the image size.

You can set the envvar **SINGULARITY\_CACHEDIR** to use other directory
than the default cache directory **$HOME/.singularity/cache**.

## Binding Paths and Mounts

On default, Singularity will map the following directories on your host
system to directories within the container:

  - $HOME
  - $PWD
  - /tmp
  - /proc
  - /sys
  - /dev

You can bind additional directories with option **-B | --bind**, such
as:

  - `-B /data`: map /data on the host to /data on the container
  - or `-B /usr/local/share:/share,/data` (please note the **comma
    delimiter**) : map /usr/local/share on the host to /share on the
    container, and map /data on the host to /data on the container.

You can also defined envvar **SINGULARITY\_BINDPATH** (such as `export
SINGULARITY_BINDPATH="/data:/mnt"`) to bind paths.

## Examples

You need define the envvar **SINGULARITY\_CACHEDIR** to a directory to
have enough space to accommodate the Singularity cache.

### Some Fun Exercise Examples

There are some fun exercises to play with the singularity command. One
simple example is "Hello World", which takes the container image from
[the Singularity container hub](https://singularity-hub.org/).

> lxplus$ singularity run shub://vsoch/hello-world INFO:
> Downloading shub image 59.75 MiB / 59.75 MiB
> \[================================\] 100.00% 35.87 MiB/s 1s INFO:
> Convert SIF file to sandbox... RaawwWWWWWRRRR\! Avocado\! INFO:
> Cleaning up image...

