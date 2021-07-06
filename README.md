# WISE-Docker-Dev

## Description
WISE development uses [Docker](https://www.docker.com/). Using Docker simplifies and standardizes the development environment so that developers can quickly and easily start developing WISE.

## Setup
1. Install Docker from [here](https://www.docker.com/products/docker-desktop).  In the Docker preferences, set the RAM to at least 5GB.
2. In the same folder, checkout [WISE-Docker-Dev (this project)](https://github.com/WISE-Community/WISE-Docker-Dev), [WISE-API](https://github.com/WISE-Community/WISE-API), and [WISE-Client](https://github.com/WISE-Community/WISE-Client).
```
$ git clone https://github.com/WISE-Community/WISE-Docker-Dev
$ git clone https://github.com/WISE-Community/WISE-API
$ git clone https://github.com/WISE-Community/WISE-Client
$ ls
WISE-Docker-Dev
WISE-API
WISE-Client
```
3. Run ```docker compose up``` in the WISE-Docker-Dev directory
```
$ cd WISE-Docker-Dev
WISE-Docker-Dev $ docker compose up
```
4. Wait for everything to download, compile, and start. This can take a while depending on your computer and connection speeds. When you see this in the output, all of the application has started:
```
...
wise-client  | ** Angular Live Development Server is listening on 0.0.0.0:4200, open your browser on http://localhost:4200/ **
wise-client  | 
wise-client  | 
wise-client  | ✔ Compiled successfully.
```
5. When you see the above output in your log output, WISE will be running at http://localhost:81. Go there with your browser to load the WISE homepage.
6. Log in with admin/pass, or previewuser/wise.

Any changes that you make to the source code will be automatically compiled and reloaded in the browser. 

## Main Docker commands
1. Start/Stop development containers
```
$ docker-compose [up/down]
```
2. List running containers
```
$ docker container ls
```
3. Restart container (ex: 'wise-client')
```
$ docker restart wise-client
```
4. Access container's command line (ex: 'wise-client')
```
$ docker exec -it wise-client sh
```
5. Run 'npm test' in wise-client container
```
$ docker exec -it wise-client npm test
```
6. Run 'npm test' in wise-client container with the watch option
```
$ docker exec -it wise-client npm test -- "--watch=true"
```
7. Run 'maven test' in wise-api container
```
$ docker exec -it wise-api mvn test
```

## MySQL Docker commands
1. Connect to MySQL container (password: iamroot)
```
$ docker run -it --network wise-docker-dev_default --rm mysql:8 mysql -hwise-mysql -uroot -p 
```
2. Import data from mysqldump
```
$ docker exec -i wise-mysql sh -c 'exec mysql wise_database -uroot -p"$MYSQL_ROOT_PASSWORD"' < ~/path_to/wise_database_dump.sql
```
3. Dump data from MySQL container
```
$ docker exec -i wise-mysql sh -c 'exec mysqldump wise_database -uroot -p"$MYSQL_ROOT_PASSWORD"' > wise_database_dump.sql
```

# Resources

Open-source license: GNU General Public License, v3.  See LICENSE.txt for details.

To see WISE in action and for inquiry science curricula developed by the WISE research team at UC Berkeley, visit https://wise.berkeley.edu.

Developer discussions: https://github.com/WISE-Community/WISE-Docker-Dev/discussions

General WISE discussions: https://wise-discuss.berkeley.edu/

