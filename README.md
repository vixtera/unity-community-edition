# What is Unity?

> Unity software significantly accelerates migration to cloud by offering one click, fully automated provisioning, scaling, upgrade and monitoring of Applications and Platforms. User can seamlessly migrate applications to the Cloud regardless of platform or infrastructure it’s running on premises. It will help IT with installed-base retention as well as creating the cloud-based application environment. Bottom line, Unity takes the big repeatable frameworks and convert them into repeatable software that takes the labor out of the process. It uses visual, portable and reusable templates that are easily connected into deployment profiles based on development, operation and service requirements and, at the push of a button, can be seamlessly deployed on premises and/or in a hybrid Cloud environment. To compliment this capability, user can transparently invoke any cloud (VMWare, OpenStack, AWS) or infrastructure (VMs, containers and bare-metal) provider to quickly deploy and manage the applications. No API, integration or coding is required while easily setting up infrastructure and then seamlessly provisioning, upgrading and scaling applications and services to the Cloud.

http://vixtera.com/

# Prerequisites

To run this application you need [Docker Engine](https://www.docker.com/products/docker-engine) >= `1.10.0`. [Docker Compose](https://www.docker.com/products/docker-compose) is recommended with a version `1.6.0` or later.

## Using Docker Compose

The recommended way to run Unity Community Edition is using Docker Compose using the following `docker-compose.yml` template:

```yaml
version: '2'
services:
  application:
    image: "vixtera/unity-app"
    ports:
     - "8080:8080"
    depends_on:
     - database
     - nexus
    environment:
     - DB_URL="database:3306/unity"
  database:
    image: "vixtera/unity-db"
    ports:
     - "3306:3306"
  nexus:
    image: "vixtera/unity-nexus"
    ports:
     - "8081:8081"     
```

Launch the containers using:

```bash
$ curl -LO https://raw.githubusercontent.com/vixtera/unity-community-edition/master/docker-compose.yml
$ docker-compose up -d
```

Default administrator credentials: 
 * username: **admin**
 * password: **admin**

## Unity CLI

Command line interface to interact with Unity server. Launch the CLI container using:

```bash
$ docker run -it vixtera/unity-cli
```

## Unity Documentation

Installation and user guides for Unity Platform:

http://doc.vixtera.com/