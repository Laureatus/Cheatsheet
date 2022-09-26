# Docker

## Working with Containers

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

## Working with Images

### Listing Images
```docker image ls```

### Deleting Images
```docker image rm alpine```





