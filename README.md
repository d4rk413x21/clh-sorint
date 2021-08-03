# Command Line Heroes

Unofficial fork of the [Command Line Heroes](https://github.com/CommandLineHeroes/clh-bash) game repository.  
This game will be used during Sorint.lab Download Festival 2021 for the "Fun" part.

## Get started

The Game is been containerized for a simply deploy in a docker or kubernetes environment.
The image is based on the official node:16.5.0 image.

### Create the image

To create a new image of clh-game follow these steps:

1. Update the clh-game directory content

2. Create the game archive by launching the following command

```bash
tar -cvzf clh-game.tar.gz --directory clh-game
```

3. Build the image

```bash
docker build -t clh-game:<tag> .
```

## Run the game

It is possible to run the game locally on Docker or in a orchestrated environment like Openshift.

### Docker Environemnt

To run the game locally in a container engine like docker

```bash
docker pull docker.io/mossicrue/clh-sorint:stable
docker run --detach --port 3000:3000 --port 3001:3001 --name clh-game mossicrue/clh-sorint:stable
```

The game will be accessible on http://localhost:3000 in your preferred browser

### Containerized Environment

To run the game in an orchestrated environment like kubernetes or openshift

```bash
kubectl apply -f clh-install.yaml
```

The all-in-one manifest will create:
- namespace
- deployment
- service
- loadbalancer
- route
