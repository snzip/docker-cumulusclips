# docker-cumulusclips

Docker container for [Cumulus Clips web application][3]

"Free Video CMS: Start your own video sharing website with CumulusClips video sharing script. It's free and easy to use. You can build a YouTube clone where users can upload videos, rate videos, comment on videos, and much more."

## Install dependencies

  - [Docker][2]

To install docker in Ubuntu 14.04 use the commands:

    $ sudo apt-get update
    $ wget -qO- https://get.docker.com/ | sh

 To install docker in other operating systems check [docker online documentation][4]

## Usage

## If you need a MySQL database you can link container :

    $ docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=mysecretpassword  -e MYSQL_DATABASE=cumulusclipsdb \
    -e MYSQL_USER=cumulusclipsdbuser -e MYSQL_PASSWORD=cumulusclipsdbpasswd -d mysql

in case you want to used pre-existing mysql container , you can add the new database by connecting to it with _docker exec -it some-mysql bash_ and manual adding cumulus clips database or you can link and used quantumobject/docker-mywebsql to create database cumulusclipsdb and user cumulusclipsdbuser plus need to grant all permision of this user to the cumulus clips database.  
  
Them link to Cumulus Clips container

    $ docker run -d -p 80 --link some-mysql:db quantumobject/docker-cumulusclips 

where when been ask for database need to replace localhost for db.

## Accessing the Cumulus Clips applications:

After that check with your browser at addresses plus the port assigined by docker or you:

  - **http://host_ip:port/**

This will create initial configuration where:

  - database : cumulusclipsdb

  - database user : cumulusclipsdbuser

  - database password : cumulusclipsdbpasswd

and after done with the final install at the web interface, need to run this command for security ..:

    $ docker exec -it container_id after_install

This will change some permission for some files internally of the container.

To access the container from the server that the container is running :

    $ docker exec -it container_id /bin/bash


## More Info

About Cumulus Clips: [cumulusclips.org][1]

To help improve this container [docker-cumulusclips][5]

[1]:http://cumulusclips.org/
[2]:https://www.docker.com
[3]:http://cumulusclips.org/
[4]:http://docs.docker.com
[5]:https://github.com/QuantumObject/docker-cumulusclips
