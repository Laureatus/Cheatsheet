# Docker

### Table of contents
[Test](https://github.com/Laureatus/Cheatsheet/blob/main/docker.md#Working-with-volumes)

## Working with Containers
<details>
  <summary>Read More</summary>
  
### Running a container

```docker container run alpine```

To create a container that gets automaticly removed when its being exited use the ```--rm``` argument.

```docker container run --rm alpine```

It is possible to set custom names for your containers. To do so use the ```--name``` argument.

```docker container run --name my_container alpine```


### Starting a shell

```docker container run -it alpine sh```

### Exit shell and leave container running

Use the key combination ```ctrl+P+Q```
This key combination will exit the container shell withoout stopping the container.

### Attach a container
To get back into a running contaienr use the following command:

```docker container attach 43049c3c3cc6```

### Stopping a container

```docker container stop 43049c3c3cc6```

### Starting the container

```docker container stop 43049c3c3cc6```

### Listing containers
Listing all running containers

```docker container ls```
Listing all containers

```docker container ls -a```

### Removing a contaier

To remove a single container use the following command.

```docker container rm 43049c3c3cc6```

To remove multiple containers at once use this command:

```docker container rm $(docker container ls -a | grep "alpine")```

This command would remove all containers that are found by grep matching the string alpine.

### Publishing a service

With the ```-p``` argument it is possible to publish the port(s) of a container to the localhost

```docker container run -p 80:80 nginx```

 </details>

## Working with Images

<details>
  <summary>Read More</summary>
  
### Login to Docker
```docker login```
  
### Pulling images
```docker image pull hello-world```
  
### Listing Images

```docker image ls```

### Deleting Images

```docker image rm alpine```
  
### Building Images
```docker image build -t myimage:latest /path/to/dockerfile```

### Tagging images
```docker image tag myimage:latest laureatus/myimage:latest```

### Pushing images 
```docker image push laureatus/myimage:latest```
  
</details>

## Working with volumes
  
  <details>
  <summary>Read More</summary>

### Bind mount a volume
If you want to access files from the localhost in the docker container it ist neccesary to link the local directory with the container.
To do so we can bind mount the directory to the container with the following command:

```docker container run -p 80:80 -v /Users/Laureatus/html:/usr/share/nginx/html nginx```
    
    
</details>
      
## Networking and Container communication
<details>
<summary>Read More</summary>

### Listing networks
```docker network ls```

### Creating a user defined network
```docker container create test```
  
### Deleting a network
```docker network rm test```
  

  
### Linking containers
To communicate between two containers they need to be in the same network or need to be linked. To link two or more containers together the following command can be used:
  
```
// Run a container with the alpine image and the came c1
docker container run --rm -it --name c1 alpine sh
  
// Run a second container named c2 and link container c1 to it.
docker container run --rm -it --name c2 --link c1 alpine sh
  
// Now you can communicate between the two containers by hostname or IP
// Test this by pinging c1 from the terminal of c2

ping c1
```


  
</details>





