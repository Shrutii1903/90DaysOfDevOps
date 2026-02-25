# Day 30 – Docker Images & Container Lifecycle

##  Overview

Today I learned how Docker images and containers work internally, including image layers, caching, and the full container lifecycle.

---

#  Task 1: Docker Images

## 1️⃣ Pull Images

```markdown

docker pull nginx
docker pull ubuntu
docker pull alpine
```
Observations:

Images are downloaded from Docker Hub.

Layers are cached locally for reuse in future builds.

Alpine is much smaller because it’s a minimal OS image.
 ## List Images
```markdown
 docker images
```
Observations:

Shows IMAGE ID, TAG, SIZE, CREATED.

Allows easy comparison of image sizes (ubuntu larger, alpine smaller).
```markdown
docker inspect nginx
```
Observations: Displays metadata: environment variables, entrypoint, layers, ports, volumes, architecture.
## Inspect Image
```markdown
docker inspect nginx
```
Observations:

Displays metadata: environment variables, entrypoint, layers, ports, volumes, architecture.
## Remove Image
```markdown
docker rmi alpine
```
Observations:

Image is deleted; disk space is freed.

Cannot remove if used by a container.
# Task 2 – Image Layers
## Image History
```docker image history nginx
```
Observations:

Each line is a layer corresponding to a Dockerfile instruction.

Layers with 0B size usually modify metadata only.

Layers are cached to make builds faster and share common parts between images.
# Task 3 – Container Lifecycle
## Create Container
```markdown
docker create --name mycontainer nginx
```
## Start Container
```markdown
docker start mycontainer
```
## Pause Container
```markdown
docker pause mycontainer
```
Observations:

Processes inside are frozen; container is listed as running with Paused status.
 ## Unpause Container
 ```markdown
docker unpause mycontainer
```
Observations:

Container resumes processes.

 ## Stop Container
 ```markdown
 docker stop mycontainer
```
Observations:

Gracefully stops container; state changes to Exited.
## Restart Container
 ```markdown
docker restart mycontainer
```
Observations:

Stops and immediately starts the container again.
## Kill Container
 ```markdown
docker kill mycontainer
```
Observations:

Forcefully terminates container immediately.
## Remove Container
 ```markdown
docker rm mycontainer
```
Observations:

Container is deleted permanently; cannot restart.
 # Task 4 – Working with Running Containers
 ##  Run Nginx in Detached Mode
  ```markdown
 docker run -d -p 8080:80 --name nginx-test nginx
```
 Observations:

Container runs in background; port 8080 mapped to container’s port 80.
## View Logs
 ```markdown
docker logs nginx-test
```
Observations:

Shows startup messages and container output.

## Real-Time Logs (Follow)
```markdown
docker logs -f nginx-test
```
Observations:

Real-time logs appear as container runs.

## Exec into Container
```markdown
docker exec -it nginx-test /bin/bash
```
Observations:

Opens interactive shell; can inspect filesystem, configs, and logs.

## Run Single Command Inside Container
```markdown
docker exec nginx-test ls /usr/share/nginx/html
```
Observations:

Executes one command without entering shell.

## Inspect Container
```
docker inspect nginx-test
```
Observations:

Shows container metadata: IP address, ports, mounts, network mode, env vars.

# Task 5 – Cleanup
## Stop All Running Containers
```
docker stop $(docker ps -q)
```
Observations:

Stops all running containers at once.

## Remove All Stopped Containers
```
docker rm $(docker ps -aq)
```
Observations:

Frees disk space; removes all exited containers.

## Remove Unused Images
```
docker image prune -a
```
Observations:

Deletes dangling/unreferenced images to free disk space.

## Check Docker Disk Usage
```
docker system df
```
Observations:

Shows disk usage by images, containers, volumes; helps identify cleanup targets.
