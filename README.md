# Docker Getting Started

## Introduction

[Docker](https://github.com/docker/docker) is a tool designed to make it easier to create, deploy, and run applications by using containers (_Standardized unit of software_).

![Overview](https://www.docker.com/sites/default/files/styles/content_6_6/public/compare/docker-containerized-appliction-blue-border.png?itok=mKnAHFYa "Docker Overview")

* [Benefits](#benefits)
* [Sample Docker file](#docker-sample)
* [Docker-compose](#docker-compose)


## <a name="benefits"></a>Popularity & Benefits of Using Docker

**Return on Investment and Cost Savings**

The first advantage of using docker is ROI. The biggest driver of most management decisions when selecting a new product is the return on investment. The more a solution can drive down costs while raising profits, the better a solution it is, especially for large, established companies, which need to generate steady revenue over the long term.

In this sense, Docker can help facilitate this type of savings by dramatically reducing infrastructure resources. The nature of Docker is that fewer resources are necessary to run the same application. Because of the reduced infrastructure requirements Docker has, organizations are able to save on everything from server costs to the employees needed to maintain them. Docker allows engineering teams to be smaller and more effective.

**Standardization and Productivity**

Docker containers ensure consistency across multiple development and release cycles, standardizing your environment. One of the biggest advantages to a Docker-based architecture is actually standardization. Docker provides repeatable development, build, test, and production environments. Standardizing service infrastructure across the entire pipeline allows every team member to work in a production parity environment. By doing this, engineers are more equipped to efficiently analyze and fix bugs within the application. This reduces the amount of time wasted on defects and increases the amount of time available for feature development.

**CI Efficiency**

Docker enables you to build a container image and use that same image across every step of the deployment process. A huge benefit of this is the ability to separate non-dependent steps and run them in parallel. The length of time it takes from build to production can be sped up notably. 

**Compatibility and Maintainability**

Eliminate the “it works on my machine” problem once and for all. One of the benefits that the entire team will appreciate is parity. Parity, in terms of Docker, means that your images run the same no matter which server or whose laptop they are running on. For your developers, this means less time spent setting up environments, debugging environment-specific issues, and a more portable and easy-to-set-up codebase. Parity also means your production infrastructure will be more reliable and easier to maintain.


**Simplicity and Faster Configurations**

One of the key benefits of Docker is the way it simplifies matters. Users can take their own configuration, put it into code, and deploy it without any problems. As Docker can be used in a wide variety of environments, the requirements of the infrastructure are no longer linked with the environment of the application.


**Rapid Deployment**

Docker manages to reduce deployment to seconds. This is due to the fact that it creates a container for every process and does not boot an OS. Data can be created and destroyed without worry that the cost to bring it up again would be higher than what is affordable.


**Continuous Deployment and Testing**

Docker ensures consistent environments from development to production. Docker containers are configured to maintain all configurations and dependencies internally; you can use the same container from development to production making sure there are no discrepancies or manual intervention.

If you need to perform an upgrade during a product’s release cycle, you can easily make the necessary changes to Docker containers, test them, and implement the same changes to your existing containers. This sort of flexibility is another key advantage of using Docker. Docker really allows you to build, test, and release images that can be deployed across multiple servers. Even if a new security patch is available, the process remains the same. You can apply the patch, test it, and release it to production.

**Multi-Cloud Platforms**

One of Docker’s greatest benefits is portability. Over last few years, all major cloud computing providers, including Amazon Web Services (AWS) and Google Compute Platform (GCP), have embraced Docker’s availability and added individual support. Docker containers can be run inside an Amazon EC2 instance, Google Compute Engine instance, Rackspace server, or VirtualBox, provided that the host OS supports Docker. If this is the case, a container running on an Amazon EC2 instance can easily be ported between environments, for example to VirtualBox, achieving similar consistency and functionality. Also, Docker works very well with other providers like Microsoft Azure, and OpenStack, and can be used with various configuration managers like Chef, Puppet, and Ansible, etc.

**Isolation**

Docker ensures your applications and resources are isolated and segregated. Docker makes sure each container has its own resources that are isolated from other containers. You can have various containers for separate applications running completely different stacks. Docker helps you ensure clean app removal since each application runs on its own container. If you no longer need an application, you can simply delete its container. It won’t leave any temporary or configuration files on your host OS. 

On top of these benefits, Docker also ensures that each application only uses resources that have been assigned to them. A particular application won’t use all of your available resources, which would normally lead to performance degradation or complete downtime for other applications.

**Security**

The last of these benefits of using docker is security. From a security point of view, Docker ensures that applications that are running on containers are completely segregated and isolated from each other, granting you complete control over traffic flow and management. No Docker container can look into processes running inside another container. From an architectural point of view, each container gets its own set of resources ranging from processing to network stacks.


## <a name="docker-sample"> Docker Sample file

```
FROM ubuntu:15.04
COPY . /app
RUN make /app
CMD python /app/app.py

```

[Other samples](https://github.com/kstaken/dockerfile-examples)

[Developing with docker](https://docs.docker.com/develop/)

[Docker tutorials](https://docs.docker.com/samples/)


## Docker compose

Compose is a tool for defining and running multi-container Docker applications. To learn more about Compose refer to the following documentation:

Check [Here](https://docs.docker.com/compose/install/) for installation instructions.

Compose sample:
```
version: '3.3'

services:
   db:
     image: mysql:5.7
     volumes:
       - db_data:/var/lib/mysql
     restart: always
     environment:
       MYSQL_ROOT_PASSWORD: somewordpress
       MYSQL_DATABASE: wordpress
       MYSQL_USER: wordpress
       MYSQL_PASSWORD: wordpress

   wordpress:
     depends_on:
       - db
     image: wordpress:latest
     ports:
       - "8000:80"
     restart: always
     environment:
       WORDPRESS_DB_HOST: db:3306
       WORDPRESS_DB_USER: wordpress
       WORDPRESS_DB_PASSWORD: wordpress
volumes:
    db_data:
```
Each compose is compatible with a specific version of docker, see [here](https://docs.docker.com/compose/compose-file/):

[Using docker-compose for you own project](https://docs.docker.com/compose/gettingstarted/#step-1-setup)

**Any Questions?**



**References**
* https://opensource.com/resources/what-docker
* https://www.docker.com/why-docker
* https://dzone.com/articles/top-10-benefits-of-using-docker