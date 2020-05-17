
![Gogs](Images/gogs.png)


Gogs is an open-source, lightweight Git server. Gogs can be used for small organizations as a code repository

It can be used in a development environment where there is a need to integrate code, perform tests, before making the project available to the public.

This process is referred in a DevOps environment as  CI/CD (Continuous Integration| Continuous Delivery).
Continuous Delivery is a practice designed to allow software to be released to production at anytime. Continuous Integration (CI) is the automation of the tasks needed to constantly integrate, test, and
deploy the work of many developers.

Within a development environment Gogs will serve as a repository for the code. In an organization many developers work on different parts of a project. Each has it's own specific task. You might say that each one contributes to a specific code functionality. But the code must work well with other parts of the code.

A simplified workflow:

* code is pushed locally
* code is integrated
* tests are performed
* code gets pushed to public


Gogs can work be installed as a local application or as a containerized application with docker. Gogs requires a Backend DB.
I choose MariaDB, but other DB are supported as well

### Local install steps

### Debian/Ubuntu

```
sudo apt-get update
sudo apt-get install git
```

### Install from binary

* https://gogs.io/docs/installation/install_from_binary

For example:

```
wget https://dl.gogs.io/0.11.91/gogs_0.11.91_linux_amd64.tar.gz 
tar -xvzf gogs_0.11.91_linux_amd64.tar.gz
```

1. cd into the directory that was just created.
2. Execute ./gogs web.

References:
* https://gogs.io/docs/installation/install_from_binary
* https://gogs.io/docs/installation/install_from_source

Install from source

### Set Up the Environment

```
sudo adduser --disabled-login --gecos 'Gogs' git
```

### Compile Gogs

```
# Clone the repository to the "gogs" subdirectory
git clone --depth 1 https://github.com/gogs/gogs.git gogs
# Change working directory
cd gogs
# Compile the main program, dependencies will be downloaded at this step
go build -o gogs
```

Cd into the directory and execute:

```
./gogs web
``` 

### DB Setup for gogs

1. Create a mysql user

```
CREATE USER 'gogs'@'localhost' IDENTIFIED BY 'admin';
GRANT ALL PRIVILEGES ON gogs. * TO 'gogs'@'localhost';
FLUSH PRIVILEGES;
```


Maria DB installation refs:
* https://www.digitalocean.com/community/tutorials/how-to-install-mariadb-on-ubuntu-18-04
* https://www.digitalocean.com/community/tutorials/how-to-create-a-new-user-and-grant-permissions-in-mysql
