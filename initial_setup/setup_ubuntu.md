# Update your system

1.  **Make the computer find out what updates are available**

    ```bash
    sudo apt update
    ```

2.  **[OPTIONAL] See for yourself what updates are available**

    ```bash
    apt list --upgradable
    ```

3.  **Install the updates (type `y` and press Enter/Return when asked)**

    ```bash
    sudo apt upgrade
    ```

<div style="page-break-after: always;"></div>

# Install Git

1.  **[OPTIONAL IF YOU HAVE DONE IT RECENTLY] Update your package list**

    ```bash
    sudo apt update
    ```

2.  **Install Git**

    ```bash
    sudo apt install git
    ```

3.  **Install GitHub CLI**

    ```bash
    (type -p wget >/dev/null || (sudo apt update && sudo apt install wget -y)) \
	&& sudo mkdir -p -m 755 /etc/apt/keyrings \
	&& out=$(mktemp) && wget -nv -O$out https://cli.github.com/packages/githubcli-archive-keyring.gpg \
	&& cat $out | sudo tee /etc/apt/keyrings/githubcli-archive-keyring.gpg > /dev/null \
	&& sudo chmod go+r /etc/apt/keyrings/githubcli-archive-keyring.gpg \
	&& sudo mkdir -p -m 755 /etc/apt/sources.list.d \
	&& echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null \
	&& sudo apt update \
	&& sudo apt install gh -y
    ```

    Command taken from Microsoft's instructions: https://github.com/cli/cli/blob/trunk/docs/install_linux.md#debian


4.  **Login to Git**

    Use the username and email ID you used to setup your Git account, instead of the examples provided here.

    ```bash
    git config --global user.name "Your Name"
    git config --global user.email "your.email@example.com"
    ```

5.  **Login to GitHub CLI**

    Make sure to login to GitHub from your web browser first.

    ```bash
    gh auth login
    gh auth setup-git
    ```

<div style="page-break-after: always;"></div>

# Setup Docker

> [!NOTE]
> Taken from instructions on Docker's page: https://docs.docker.com/engine/install/ubuntu/

1.  Remove old packages
    
    ```bash
    sudo apt remove $(dpkg --get-selections docker.io docker-compose docker-compose-v2 docker-doc podman-docker containerd runc | cut -f1)
    ```

2.  Setup Docker's apt repository

    ```bash
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
    ```

3.  Install Docker

    ```bash
    sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
    ```

4.  Add yourself to the docker group and restart

    ```bash
    sudo usermod -aG docker $USER
    sudo reboot now
    ```

5.  Test the Docker installation

    ```bash
    docker run hello-world
    ```