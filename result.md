# result
p72

## docker-compose pull

```
# docker-compose pull
Pulling zookeeper    ... done
Pulling mesos-master ... done
Pulling mesos-slave  ... done
Pulling marathon     ... done
```

## docker-compose up -d

```
# docker-compose up -d
Creating network "mesos-marathon-demo_app_net" with driver "bridge"
Creating mesos-marathon-demo_zookeeper_1 ... done
Creating mesos-marathon-demo_mesos-master_1 ... done
Creating mesos-marathon-demo_mesos-slave_1  ... done
Creating mesos-marathon-demo_marathon_1     ... done
```

## docker ps

```
# docker ps
CONTAINER ID        IMAGE                           COMMAND                  CREATED             STATUS              PORTS                                        NAMES
40e7caf7cf97        mesosphere/marathon:v1.5.6      "./bin/start --disab…"   22 seconds ago      Up 22 seconds       0.0.0.0:8080->8080/tcp                       mesos-marathon-demo_marathon_1
0efb7f1b907e        mesosphere/mesos-slave:1.4.1    "mesos-slave"            22 seconds ago      Up 23 seconds       0.0.0.0:5051->5051/tcp                       mesos-marathon-demo_mesos-slave_1
2ba473d0de31        mesosphere/mesos-master:1.4.1   "mesos-master --regi…"   23 seconds ago      Up 24 seconds       0.0.0.0:5050->5050/tcp                       mesos-marathon-demo_mesos-master_1
f17b0768a91c        zookeeper:3.4.11                "/docker-entrypoint.…"   24 seconds ago      Up 24 seconds       2888/tcp, 0.0.0.0:2181->2181/tcp, 3888/tcp   mesos-marathon-demo_zookeeper_1
⋊> ~/g/mesos-marathon-d
```

## exec sample application

```
# ./sample/hello-world.sh
{"id":"/hello-world","backoffFactor":1.15,"backoffSeconds":1,"container":{"type":"DOCKER","docker":{"forcePullImage":false,"image":"dockercloud/hello-world","parameters":[{"key":"memory","value":"32m"}],"privileged":false},"volumes":[],"portMappings":[{"containerPort":80,"hostPort":0,"labels":{},"protocol":"tcp","servicePort":0}]},"cpus":0.1,"disk":0,"executor":"","instances":1,"labels":{},"maxLaunchDelaySeconds":600,"mem":16,"gpus":0,"networks":[{"mode":"container/bridge"}],"requirePorts":false,"upgradeStrategy":{"maximumOverCapacity":1,"minimumHealthCapacity":1},"version":"2018-04-27T11:00:00.011Z","killSelection":"YOUNGEST_FIRST","unreachableStrategy":{"inactiveAfterSeconds":0,"expungeAfterSeconds":0},"tasksStaged":0,"tasksRunning":0,"tasksHealthy":0,"tasksUnhealthy":0,"deployments":[{"id":"06a7f6a1-a453-46cf-80a1-7ba3cbbb1f19"}],"tasks":[]}⏎
```

## claen

```
# docker-compose down
Stopping mesos-marathon-demo_marathon_1     ... done
Stopping mesos-marathon-demo_mesos-slave_1  ... done
Stopping mesos-marathon-demo_mesos-master_1 ... done
Stopping mesos-marathon-demo_zookeeper_1    ... done
Removing mesos-marathon-demo_marathon_1     ... done
Removing mesos-marathon-demo_mesos-slave_1  ... done
Removing mesos-marathon-demo_mesos-master_1 ... done
Removing mesos-marathon-demo_zookeeper_1    ... done
Removing network mesos-marathon-demo_app_net
```
