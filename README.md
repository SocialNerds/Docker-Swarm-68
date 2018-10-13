# Docker Swarm Example with Docker Compose 

Run Swarm and local docker containers on the same docker compose files.

# Check the full explanation video (GR)
[![Docker Swarm, για Σοβαρό DevOps #68, live](https://img.youtube.com/vi/LS3UipRxAVs/0.jpg)](https://www.youtube.com/watch?v=LS3UipRxAVs)

# Installation
Requirements
- You need to have [Docker](https://docs.docker.com/engine/installation/) installed

# Run
## Run without Swarm
Run in root folder,
~~~~
cp .env.example .env
docker-compose -f docker-compose.yml -f docker-compose-dev.yml build
docker-compose -f docker-compose.yml -f docker-compose-dev.yml up -d
~~~~

Login to the container,
~~~~
docker exec -u serveruser -it dockernerds_fpm /bin/bash -c "TERM=$TERM exec bash"
~~~~

Exit the container,
~~~~
exit
~~~~

You may also want to check your browser: http://127.0.0.1

Remove the containers,
~~~~
docker-compose -f docker-compose.yml -f docker-compose-dev.yml down
~~~~

## Run in Swarm

Be sure to remove previous containers,
~~~~
docker-compose -f docker-compose.yml -f docker-compose-dev.yml down
~~~~

Start Registry,
~~~~
cd registry
docker-compose build && docker-compose up -d
cd ..
~~~~

Build images and push them to local registry,
~~~~
docker-compose -f docker-compose.yml -f docker-compose-dev.yml build
docker-compose -f docker-compose.yml -f docker-compose-dev.yml push
~~~~

Start Swarm,
~~~~
docker swarm init
~~~~

Deploy stack,
~~~~
docker stack deploy --compose-file=<(docker-compose --file docker-compose.yml config) --compose-file docker-compose-prod.yml dockernerds_swarm
~~~~

Enjoy the powahhhh!
~~~~
docker service ls
docker service scale dockernerds_swarm_fpm=5
~~~~

You may also want to check your browser: http://127.0.0.1

Shut down everything,
~~~~
docker stack rm dockernerds_swarm
docker swarm leave --force
cd registry
docker-compose down
cd ..
~~~~

# By SocialNerds
* [SocialNerds.gr](https://www.socialnerds.gr/)
* [YouTube](https://www.youtube.com/SocialNerdsGR)
* [Facebook](https://www.facebook.com/SocialNerdsGR)
* [Twitter](https://twitter.com/socialnerdsgr)