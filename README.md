# How to update your Dockerfile image in docker-compose.yml

This repository shows how to solve a little problem that I face while I'm developing a new Docker image for my projects.
The problem is update a custom image that you're building in your docker-compose.

### Running the containers
To understand the problem you must run the project.
You can run all containers
```shell
docker-compose up
```
or run only a service:
```shell
docker-compose run --rm app
```

### The problem

Change the current CMD text in Dockerfile
```shell
CMD ["echo", "Hello world!" ]
```

To anything else like:
```shell
CMD ["echo", "Too lazy to write descriptive message" ]
```

After update the text try to run your container again
```shell
docker-compose up
```
or 
```shell
docker-compose run --rm app
```

And it didn't updated the text... 🥲

### Solution 🍀
Everytime you change the image that you're building, you must build the images again running the comando below:

```shell
docker-compose up --build
```

After this your container is correctly updated with the correct image!