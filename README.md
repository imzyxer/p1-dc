#  Docker Compose for P1

##  Installation
 
* Clone this repository on your local computer
* configure .env as needed 
* Run the `docker-compose up -d`.

Your LAMP stack is now ready!! You can access it via `http://localhost`.


#### Connect via SSH

You can connect to web server using `docker-compose exec` command to perform various operation on it. Use below command to login to container via ssh.

```shell
docker-compose exec webserver bash
```

## PHP

The installed version of depends on your `.env` file. 

#### Extensions

> If you want to install more extension, just update `./docker/php81/Dockerfile`.
> You have to rebuild the docker image by running `docker-compose build` and restart the docker containers.
