# Docker Swarm Cluster with Tomcat Stack
This project demonstrates the setup of a Docker Swarm cluster with 2 worker nodes and deployment of a Tomcat stack using tomcat:8.0 image. The stack is configured with specific requirements such as resource limits, update policies, and restart conditions.

# Requirements
* Docker
* Docker Swarm initialized with 1 manager and 2 worker nodes

# Setup Instructions
### Step 1: Initialize Docker Swarm
On the manager node, initialize Docker Swarm:
```
docker swarm init
```
Add worker nodes to the Swarm:

```
docker swarm join-token worker
```

This command will provide a token. Run the provided token command on each worker node to join them to the Swarm.

### Step 2: Clone stack.yml File

### Step 3: Deploy the Stack
Deploy the stack to the Docker Swarm:
```
docker stack deploy -c stack.yml tomcat-stack
```

### Step 4: Verify the Deployment
Check the services:
```
docker service ls
```

Inspect the status of the tomcat service:
```
docker service ps tomcat-stack_tomcat
```

### Additional Step
Set a maximum number of replicas per node:
```
docker service update --replicas-max-per-node=3 tomcat-stack_tomcat
```
