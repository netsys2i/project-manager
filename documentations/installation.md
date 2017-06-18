Installation
============

Requirements
------------

Before anything, you need the following software installed on your machine:

  * [Node](https://nodejs.org/en/download/current/) >= 6
  * [Docker](https://docs.docker.com/engine/installation/)
  * [Docker Compose](https://docs.docker.com/compose/install/)
  * [Ansible](http://docs.ansible.com/ansible/intro_installation.html#installing-the-control-machine)

Project installation
--------------------
To install the project, you must at first the code repository:
``` bash
    git clone git@github.com:theodo/pepiniere-gedsegl-elvis.git
```

Then, this project can be installed by running the install script:
``` bash
    cd pepiniere-gedsegl-elvis/
    git submodule update --recursive --init
    npm install
    docker login -u PepiniereRegistryUser -p LetMeInThePepiniereRegistry https://registry.pepinie.re:5000
```

Application initialisation
--------------------------

Once you have everything required, you must:

``` bash
    docker-compose up
```

Because of the MMMagic library, the server will not work yet.
To fix this problem, you must rebuild the dependencies from the inside of the docker container.
Open a new terminal and run:

``` bash
docker-compose exec server npm rebuild
```

Hosts configuration
-------------------

For more convenience, setup local hosts on your **host machine**

```
sudo /bin/bash -c 'echo "localhost  elvis.dev" >> /etc/hosts'
```

Now you should be able to access the application in your Web browser:
  * Use https://elvis.dev:8030/elvis/ for local environment (need Docker container to be up)


SSH configuration
-----------------

From your **host machine**, generate and add (if needed) an SSH key pair:
```
ssh-keygen -f ~/.ssh/rsa_elvis
ssh-add ~/.ssh/rsa_elvis
```

Then copy-paste the following SSH configuration in your ***~/.ssh/config***, and replace `%pepiniere-gedsegl%` by the root directory of the project:
```
Host sg-m4
    Hostname m4.pepinie.re
    User centos
    IdentityFile %pepiniere-gedsegl-elvis%/provisioning/ansible/SG-STNULX04
    ForwardAgent yes

Host sg-m4-edge
   Hostname m4-edge.pepinie.re
   User appli
   IdentityFile %pepiniere-gedsegl-elvis%/provisioning/ansible/SG-STNULX04
   ForwardAgent yes

Host sg-m4-edge-centos
   Hostname m4-edge.pepinie.re
   User centos
   IdentityFile %pepiniere-gedsegl-elvis%/provisioning/ansible/SG-STNULX04
   ForwardAgent yes
```

If you need to access the sg-documentum VM, ask for someone to put your ssh public key in it

You will also need to restrict permissions of the private key needed to access m4:
`chmod 600 %pepiniere-gedsegl-elvis%/provisioning/ansible/SG-STNULX04`
