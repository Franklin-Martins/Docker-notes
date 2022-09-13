# Docker-notes, using mysql database
 docker sketches and annotations
 
 ### To start any docker:
  `sudo docker start <container name or container id>`
 
 ### In case of a create connection to a database:
  #### Verify the host of docker with:
   `sudo docker inspect <container name or container id> | grep IPAddress`
  #### Should return something like:
    `"SecondaryIPAddresses": null,
            "IPAddress": "",
                    "IPAddress": "172.21.0.1",`
 ### Then, with the ip you can manage the database inside of container with:
   `sudo docker exec -it <container name or container id> /bin/bash`
   #### after:
   `mysql -h 172.21.0.2 -P 3306 -u root -p`

### In case you want import an .sql to your database:
  `sudo docker exec -i <container name> sh -c 'exec mysql -uroot -p"$MYSQL_ROOT_PASSWORD"' < ~/PATH_TO_FILE/<filename>.sql`

### In case you want export your database:
  `docker exec some-mysql sh -c 'exec mysqldump --all-databases -uroot -p"$MYSQL_ROOT_PASSWORD"' > ~/PATH_TO_FILE/<filename>.sql`

References:
[Oficial Docker Hub](https://hub.docker.com/_/mysql)
