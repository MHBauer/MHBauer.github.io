---
layout: post
title:  "docker swarm sequencing"
date:   2015-08-20
categories: docker swarm machine
---

The combination of docker, swarm, and machine has a lot of moving parts to keep track of.

docker binary is both a client and a server, depending on the invocation

* docker daemon - runs the daemon, only applicable to run on the server.
* docker * - any other command is a client command used to talk to the daemon running on the host server.

swarm binary is both a client and a server, depending on the invocation. The swarm image is simply the swarm executable packaged in a container so it is easy to run. It is equally valid to run swarm outside of a container.

* swarm create - uses the serivce provided by Docker to create a token. Not needed for other ways to cluster nodes like etcd.
* swarm list - needs to talk to an endpoint running manager.
  This can run on any machine, even a local laptop without any other docker tools.
* swarm join - registers with the discovery service periodically.
  The address being registered with is the address of the Docker Daemon running on the Host.
  Heartbeat flag is the time between registrations in seconds.
  This needs to run on an endpoint that is a host server with docker.
* swarm manage -  host server command that starts a webserver with the Docker api.
  talks to the managed nodes. The managed nodes need to be running `docker daemon`.
  `swarm manage -H` is like `docker daemon -H`.
  You are specifying the IP and port to listen for connections from,
  so typically that is 0.0.0.0 to listen for connections from any IP,
  and a specific port like 3376 (which is a take on the original docker tls port of 2376).

Docker is used to talk to the swarm manager. The manager talks to each
node, and each node is the docker daemon running on the host. Thus,
the manager is a both a server and a client. It is a server to the
docker client used by the user, and a client to the docker daemons in
the swarm.


![swarm communication diagram]({{ site.url }}/images/swarm diagram.png)
