
# Mautic Setup Guide on Amazon EC2 Ubuntu

This guide provides a step-by-step instruction for setting up [Mautic](https://www.mautic.org/) on an Amazon EC2 Ubuntu instance. We'll use Docker to make the process easier and more reproducible.

**Table of Contents**
- [Update the APT package index](#update-the-apt-package-index)
- [Install necessary packages](#install-necessary-packages)
- [Add Docker's official GPG key](#add-dockers-official-gpg-key)
- [Verify the GPG key](#verify-the-gpg-key)
- [Add Docker's official APT repository](#add-dockers-official-apt-repository)
- [Update the APT package index again](#update-the-apt-package-index-again)
- [Install Docker Engine, containerd, and Docker Compose](#install-docker-engine-containerd-and-docker-compose)
- [Create a new directory for your project](#create-a-new-directory-for-your-project)
- [Navigate to your new directory](#navigate-to-your-new-directory)
- [Create a new docker-compose.yml file](#create-a-new-docker-composeyml-file)
- [Save and close the file](#save-and-close-the-file)
- [Install Docker Compose using APT](#install-docker-compose-using-apt)
- [Add your user to the docker group](#add-your-user-to-the-docker-group)
- [Run the Mautic Docker Application](#run-the-mautic-docker-application)

## Update the APT package index
Open your terminal and run the following command:

```bash
sudo apt-get update
```

## Install necessary packages
Docker requires some pre-requisite packages to set up the Docker repository. Install them with:

```bash
sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
```

## Add Docker's official GPG key

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

## Verify the GPG key

```bash
sudo apt-key fingerprint 0EBFCD88
```

It should display a key fingerprint that ends with `9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88`.

## Add Docker's official APT repository
To add the stable Docker repository to your system, use the following command:

```bash
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```

## Update the APT package index again
Now, your system should know where to find Docker packages.

```bash
sudo apt-get update
```

## Install Docker Engine, containerd, and Docker Compose
You can install these packages by running the following command in your terminal:

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

## Create a new directory for your project
This can be done with the mkdir command, followed by the name of your directory:

```bash
mkdir my_docker_project
```

## Navigate to your new directory
You can use the cd command to change to your newly created directory:

```bash
cd my_docker_project
```

## Create a new docker-compose.yml file
Use a text editor to create a new docker-compose.yml file. Here's an example using nano:

```bash
nano docker-compose.yml
```
You can find the content of this file [here](https://github.com/ZanVanSer/Mautic-Docker/blob/main/docker-compose.yml).

## Save and close the file
In nano, you can do this by pressing `Ctrl + X`, then `Y` to confirm that you want to save the changes, and then `Enter` to confirm the file name.

## Install Docker Compose using APT
Run the following command to install Docker Compose:

```bash
sudo apt install docker-compose
```

Once the installation is complete, you can confirm that it was successful by checking the version of Docker Compose:

```bash
docker-compose --version
```

## Add your user to the docker group
```bash
sudo usermod -aG docker $USER
```

## Run the Mautic Docker Application 
```bash
sudo docker-compose up
```
After this, go to the server public IP and continue setup in the browser.

---

Remember to replace `$USER` with your username and use your own IP when setting up in the browser. Enjoy using Mautic!
