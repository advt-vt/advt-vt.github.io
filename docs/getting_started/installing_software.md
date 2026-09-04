---
title: Installing Software
description: Install Required Software.
---

# <p style="text-align: center"> Installing Software </p>

---

## <p style="text-align: center"> Windows </p>

### Installing [WSL](https://learn.microsoft.com/en-us/windows/wsl/install)

Open command prompt **as an administrator** and run the following commands.

``` sh
wsl.exe --install -d Ubuntu-24.04
wsl --set-default Ubuntu-24.04
```

Enter your user info to complete the installation.

### Installing [Docker Desktop](https://docs.docker.com/desktop/setup/install/windows-install/)

Go to this link <https://docs.docker.com/desktop/setup/install/windows-install/> and download and install Docker Desktop for Windows.

Then open Ubuntu in WSL and add yourself to the docker user group.

``` bash
sudo apt update
sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker
```

Ensure the [WSL 2 back-end](https://aka.ms/vscode-remote/containers/docker-wsl2) is enabled. Open Docker Desktop and select **Settings**. Enable Ubuntu-24.04 under **Resources > WSL Integration**. Then click **Apply & Restart**.

### Installing [VS Code](https://code.visualstudio.com/Download)

Go to this link <https://code.visualstudio.com/Download> and download and install VS Code for Windows.

### Installing [Git](https://git-scm.com/install/windows)

(or should we just use github desktop?) (do we even need to? does it come in wsl?) (also potentially seperate windows and linux into seperate pages, so headers are better, make subheaders in the middle)

Go to this link <https://git-scm.com/install/windows> and download and install the latest version.

<br>

## <p style="text-align: center"> Linux </p>

The commands provided here are for Ubuntu. If you are using a different distribution (including Debian!!) follow the official instructions for each part linked in the header.

### Installing [Git](https://git-scm.com/install/linux)

Run this in a terminal.

``` bash
sudo apt update
sudo apt install git -y
```

### Installing [Docker Engine](https://docs.docker.com/engine/install/)

Run the following commands in a terminal.

``` bash
# Uninstall unofficial packages
sudo apt remove $(dpkg --get-selections docker.io docker-compose docker-compose-v2 docker-doc docker-buildx podman-docker containerd runc | cut -f1)

# Add Docker's official GPG key:
sudo apt update
sudo apt install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/ubuntu
Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
Components: stable
Architectures: $(dpkg --print-architecture)
Signed-By: /etc/apt/keyrings/docker.asc
EOF

sudo apt update

# Install Docker
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

``` bash
# Start docker
sudo systemctl enable docker
sudo systemctl start docker

# Create and add yourself to the docker user group
sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker
```

``` bash
# Restart
systemctl reboot
```

### Installing [VS Code](https://code.visualstudio.com/Download)

Go to this link <https://code.visualstudio.com/Download> and download the latest build of VS Code for your distribution and architecture. Then run this command to install it.

```bash
sudo apt install ~/Downloads/code_*.deb
```
