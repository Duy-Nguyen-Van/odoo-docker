# odoo-docker
Install Odoo with Docker

1. Install Docker CE [1]
    Install using the repository

    Before you install Docker CE for the first time on a new host machine, you need to set up the Docker repository. Afterward, you can install and update Docker from the repository.

    SET UP THE REPOSITORY

    Update the apt package index:
    ```
    $ sudo apt-get update
    ```
    Install packages to allow apt to use a repository over HTTPS:
    ```
    $ sudo apt-get install \
        apt-transport-https \
        ca-certificates \
        curl \
        gnupg2 \
        software-properties-common
    ```
    Add Docker’s official GPG key:
    ```
    $ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    ```
    Verify that you now have the key with the fingerprint 9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88, by searching for the last 8 characters of the fingerprint.
    ```
    $ sudo apt-key fingerprint 0EBFCD88

    pub   4096R/0EBFCD88 2017-02-22
        Key fingerprint = 9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
    uid                  Docker Release (CE deb) <docker@docker.com>
    sub   4096R/F273FCD8 2017-02-22
    ```
    Use the following command to set up the stable repository. You always need the stable repository, even if you want to install builds from the edge or test repositories as well. To add the edge or test repository, add the word edge or test (or both) after the word stable in the commands below.
    ```
    $ sudo add-apt-repository \
        "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
        $(lsb_release -cs) \
        stable"
    ```
    
    INSTALL DOCKER CE
    Update the apt package index.
    ```
    $ sudo apt-get update
    ```
    Install the latest version of Docker CE, or go to the next step to install a specific version:
    ```
    $ sudo apt-get install docker-ce
    ```
    To install a specific version of Docker CE, list the available versions in the repo, then select and install:
    a. List the versions available in your repo:
        ```
        $ apt-cache madison docker-ce

        docker-ce | 5:18.09.1~3-0~ubuntu-xenial | https://download.docker.com/linux/ubuntu  xenial/stable amd64 Packages
        docker-ce | 5:18.09.0~3-0~ubuntu-xenial | https://download.docker.com/linux/ubuntu  xenial/stable amd64 Packages
        docker-ce | 18.06.1~ce~3-0~ubuntu       | https://download.docker.com/linux/ubuntu  xenial/stable amd64 Packages
        docker-ce | 18.06.0~ce~3-0~ubuntu       | https://download.docker.com/linux/ubuntu  xenial/stable amd64 Packages
        ...
        ```
    b. Install a specific version using the version string from the second column, for example, 5:18.09.1~3-0~ubuntu-xenial.
        ```
        $ sudo apt-get install docker-ce=<VERSION_STRING>
        ```
    Verify that Docker CE is installed correctly by running the hello-world image.
    ```
    $ sudo docker run hello-world
    ```

2. Install Docker Compose [2]
    Run this command to download the latest version of Docker Compose:
    ```
    sudo curl -L "https://github.com/docker/compose/releases/download/1.23.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
    ```
    Apply executable permissions to the binary:
    ```
    sudo chmod +x /usr/local/bin/docker-compose
    ```
    Test the installation.
    ```
    $ docker-compose --version
    docker-compose version 1.23.2, build 1110ad01
    ```

3. Install Odoo [3]
    ```
    sudo docker pull odoo:<version>
    ```

4. Install Postges [4]
    ```
    sudo docker pull postgres:<version>
    ```

5. Create new directory
    ```
    sudo mkdir <dir_name>
    ```

6. Copy docker-compose.yml to directory

7. Run docker
    ```
    sudo docker-compose up 
    ```
REFERENCE
[1] Install Docker: https://docs.docker.com/install/linux/docker-ce/ubuntu/

[2] Install Docker Compose: https://docs.docker.com/compose/install/#install-compose

[3] Install Odoo: https://hub.docker.com/_/odoo

[4] Install Postgres: https://hub.docker.com/_/postgres