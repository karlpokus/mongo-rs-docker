# mongo-rs-docker
Single-, and multi-node mongodb replica set in docker. See https://hub.docker.com/_/mongo for custom configs.

The entrypoint of the mongo image is created to pass its arguments along to mongod. List all options with `docker run -it mongo:4.0.3 --help`

# multi-node
```bash
# create shared network
$ docker network create mongo-rs
# run containers
$ docker run --name mongo-0{1..3} -d --net mongo-rs mongo:4.0.3 --replSet rs0
# initiate rs in mongo shell
$ docker exec -it mongo-01 mongo
> rs.initiate()
# check rs state with rs.conf() and rs.status()
> rs.add("mongo-02")
> rs.add("mongo-03")
> exit
```

# single-node
```bash
$ docker-compose up
```

# license
MIT
