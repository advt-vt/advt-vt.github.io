---
title: Installing PX4
description: Installing PX4 if needed
---

# <p style="text-align: center"> Installing PX4 </p>

!!! Note "Windows Users"
    **If you are using Windows you must do all of the following commands in WSL**

First OUTSIDE of the dev container add `ADVT_PX4_INSTALL=true` into your .bashrc.

``` bash
echo "export ADVT_PX4_INSTALL=true" >> ~/.bashrc
```

Then pull the PX4 main repository and all of its sub repos.

``` bash
cd ~/advt && git clone https://github.com/PX4/PX4-Autopilot.git --recursive
```

Then close VS Code and reopen and rebuild the container and PX4 should be setup.
