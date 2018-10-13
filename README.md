# Docker Swarm Example with Docker Compose 

Run swarm and local docker containers on the same docker compose files.

# Check the full explanation video (GR)
[![Docker Swarm, για Σοβαρό DevOps #68, live](https://img.youtube.com/vi/LS3UipRxAVs/0.jpg)](https://www.youtube.com/watch?v=LS3UipRxAVs)

# Installation
Requirements
- You need to have [Docker](https://docs.docker.com/engine/installation/) installed

# Run
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

# By SocialNerds
* [SocialNerds.gr](https://www.socialnerds.gr/)
* [YouTube](https://www.youtube.com/SocialNerdsGR)
* [Facebook](https://www.facebook.com/SocialNerdsGR)
* [Twitter](https://twitter.com/socialnerdsgr)