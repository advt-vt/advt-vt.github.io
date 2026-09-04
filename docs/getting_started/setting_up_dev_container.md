---
title: Dev Container
description: Setting up the development container.
---

# <p style="text-align: center;"> Setting up the Development Container </p>

## <p style="text-align: center;"> Cloning the Repository </p>

First create a new SSH key. Use the default path (~/.ssh/id_ed25519), you can set a passphrase if you want (if you do make it short as you will need to enter it every time you use the key).

!!! Note "Windows Users"
    **If you are using Windows you must do all of the following commands in WSL**

!!! Note "Linux Users"
    If you already have a ssh key added to your github account you can skip to the end of this step.

``` bash
ssh-keygen -t ed25519 -C "github"
cat ~/.ssh/id_ed25519.pub
```

Go to this link <https://github.com/settings/keys> and click **New SSH Key**. Add the title `WSL Ubuntu 24.04` and copy the ~/.ssh/id_ed25519.pub file contents (printed above) to the key field.

Then open your ssh config file by running this command.

``` bash
nano ~/.ssh/config
```

And then paste this block into the file.

``` bash
Host github.com
    IdentityFile ~/.ssh/id_ed25519
```

Then clone the repository and open VS Code.

``` bash
git clone git@github.com:advt-vt/advt.git && cd advt && code .
```

## <p style="text-align: center;"> Installing the dev container </p>

In VS Code open the Quick Open Dialog by pressing `Ctrl+P`/`⌘P`.

Type `ext install dev containers` and install and enable the Microsoft Dev Containers extension.

Build and enter the dev container by opening the Quick Open Dialog and typing `>Dev Containers: Rebuild and Reopen in Container`.

## <p style="text-align: center;"> Reopening the Container </p>

To stop the container open the Quick Open Dialog box and type `Remote: Close Remote Connection` and then close VS Code.

To reopen the container first open WSL and run this command.

``` bash
cd advt && git pull && code .
```

Then reopen the container by opening the Quick Open Dialog box and typing `>Dev Containers: Rebuild and Reopen in Container`.

## <p style="text-align: center;"> [Known Limitations](https://code.visualstudio.com/docs/devcontainers/containers#_known-limitations) of Dev Containers </p>

* The unofficial Ubuntu Docker snap package for Linux is not supported.
* Docker Toolbox on Windows is not supported.
* Local proxy settings are not reused inside the container, which can prevent extensions from working unless the appropriate proxy information is configured (for example global `HTTP_PROXY` or `HTTPS_PROXY` environment variables with the appropriate proxy information).
* There is an incompatibility between OpenSSH versions on Windows when the ssh-agent runs with version <= 8.8 and the SSH client (on any platform) runs version >= 8.9. The workaround is to upgrade OpenSSH on Windows to 8.9 or later, either using winget or an installer from [Win32-OpenSSH/releases](https://github.com/PowerShell/Win32-OpenSSH/releases). (Note that `ssh-add -l` will work correctly, but `ssh <ssh-server>` will fail with `<ssh-server>: Permission denied (publickey)`. This also affects Git when using SSH to connect to the repository.)
