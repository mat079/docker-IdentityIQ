# Docker-IdentityIQ
Deploy an IdentityIQ instance using Docker.

This project use docker-compose to deploy an MySQL container and an Apache Tomcat container.

## Requirements

To use this project, you must download and install [Docker](https://www.docker.com/get-started), and have an IdentityIQ zip archive of your choice from [Compass](https://community.sailpoint.com/t5/IdentityIQ-Server-Software/ct-p/IdentityIQ).

## Setup

Before running any commands, you have to deposite your IdentityIQ zip archive in the root of the directory project. Then you must edit the **docker-compose.yml** file and update the **IIQ_VERSION** arg by the version you are using. *(Exemple : 8.2 for identityiq-8.2.zip)*

Then, go to the root of the directory and run `docker-compose up`. This command will build the docker-identityiq_tomcat image and create the iiq-mysql and iiq-tomcat containers.

At the first launch, the iiq-tomcat container will install mariadb client to communicate with the mysql container, and run the *create_identityiq_tables-\<version\>.sql* script. Then it will run the iiq console, import init files and start the tomcat server.

![first-launch](https://user-images.githubusercontent.com/23320254/149496381-6e65d475-3312-4f7b-acbc-33131798ecf9.png)
  
After that, the iiq-tomcat container will launch tomcat server after each start.

## Usage

To stop the containers, use the command `docker-compose stop`.

To start the containers, use the command `docker-compose start`.

To remove the containers, use the command `docker-compose down`.

To recreate the containers, use the command `docker-compose up`.
