# Docker for PHP development
### Fast-setup

1. Install docker: https://www.docker.com/ @unix: Be sure to install docker-compose and configure a DNS server on 192.168.99.100.
2. After cloning the repository, copy the file "default.env" to a new file named ".env".
3. Check the default values and change them as needed. @windows: Pay special attention to the local path, as it needs to be on your Users folder.
4. Open your hosts file and add a line for the new host. By default: 192.168.99.100    virtualhost.dev
5. Open the terminal (docker terminal if you are on windows) and cd to the cloned repository folder.
6. Execute the following command:

```
$ docker-compose up -d
```

7. Copy/clone your code to the local path you chose and navigate to the host path you chose. The site should be working.

### Usage
#### Mysql configuration
You can access the server from your computer or any container using the following data:

* user: root
* password: root
* ip: 192.168.99.100
* port: 3307 (Do not forget to specify the port)

In SSH : ```mysql -uroot -proot -h 192.168.99.100 -P 3307```


#### SSH access
You can access your server by ssh by using the following data:

* user: root
* password: root
* ip: 192.168.99.100
* port: Use the port you set on the .env file.

#### Docker cheatsheet
If you followed the fast-setup you probably already have a working site. However, as we work with different projects we need to have more than one site ready to use and we must know some basic commands in order to manage the containers on the long run.

* To get the list of current active containers:

```
$ docker ps
```

* To get the list of all the created containers (active or inactive):

```
$ docker ps -a
```

* To start a new container using docker-composer (more advanced users could also use docker run directly):
1. Change the variable values on the .env file since they will be read again.
2. Run:

```
$ docker-compose run -d webserver
```

* To start a docker container (to obtain the name use docker ps -a):

```
$ docker start [container_name]
```

* To stop a docker container (to obtain the name use docker ps -a):

```
$ docker stop [container_name]
```

* To remove a stopped docker container (to obtain the name use docker ps -a):

```
$ docker rm [container_name]
```

* To remove a docker image (to obtain the name use docker ps -a):

```
$ docker rmi [image_name]
```


#### ADVANCED: Docker cheatsheet
* To create another container with existing image resulting from docker-compose (to get your image_name, run a docker ps):

```
$ docker run -d -p 8027:22 -e VIRTUAL_HOST=laravel.dev -v /c/Users/jrmartinez/workspace/laravel/htdocs:/var/www --name laravel [image_name]
```

* To connect to a docker container without using ssh (useful if you need to connect to the nginx machine for example):

```
$ docker exec -i -t nginx /bin/bash
```

