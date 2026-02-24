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
