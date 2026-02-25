# Day 31 – Dockerfile: Build Your Own Images

## Task 1 – Your First Dockerfile

**Folder:** `my-first-image`  

**Dockerfile:**

```dockerfile
FROM ubuntu:latest
RUN apt update && apt install -y curl
CMD ["echo", "Hello from my custom image!"]
```

Build and run:

```docker build -t my-ubuntu:v1 .
docker run my-ubuntu:v1
# Output: Hello from my custom image!
```

Observation:

Created a simple image using Ubuntu.

Learned how CMD sets a default message.

Building and running a container shows that your image works.

## Task 2 – Dockerfile Instructions

Folder: dockerfile-instructions

app.txt:
```
Hello from Dockerfile instructions example.
```

Dockerfile:

```
FROM ubuntu:latest
RUN apt update && apt install -y curl
WORKDIR /app
COPY app.txt .
EXPOSE 8080
CMD ["cat", "app.txt"]
```
Build and run:

```
docker build -t instructions:v1 .
docker run instructions:v1
# Output: Hello from Dockerfile instructions example.
```

Observation:

Learned all important Dockerfile instructions:

FROM → base image

RUN → commands to set up image

WORKDIR → where commands run inside image

COPY → move files into image

EXPOSE → document port

CMD → default command

Using a separate folder avoids confusion with other Dockerfiles.

## Task 3 – CMD vs ENTRYPOINT

CMD Example:

```
FROM ubuntu:latest
CMD ["echo", "hello"]
```

Default run: prints hello

Can override by running: docker run cmd-image echo overridden → prints overridden

ENTRYPOINT Example:

```
FROM ubuntu:latest
ENTRYPOINT ["echo"]
```

Always runs echo

Can pass arguments: docker run entrypoint-image overridden → prints overridden

Observation:

CMD = default command (replaceable)

ENTRYPOINT = mandatory command (arguments can be added)

Combining CMD + ENTRYPOINT gives flexibility.

## Task 4 – Build a Simple Web App Image

Folder: my-website
```
index.html:

<!DOCTYPE html>
<html>
<head>
  <title>My Docker Website</title>
</head>
<body>
  <h1>Hello from my Nginx Docker container!</h1>
</body>
</html>
```
Dockerfile:
```
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
EXPOSE 80
```
Build and run:
```
docker build -t my-website:v1 .
docker run -d -p 80:80 my-website:v1
# Access in browser: http://YOUR_PUBLIC_IP
```
Observation:

Learned how to serve a static website using Docker + Nginx.

Copying HTML into the image makes it available in the container.

-p 80:80 maps the container port to EC2 so the browser can see it.

Common issue: “port already allocated” → another container or process is using the same port.

## Task 5 – .dockerignore

.dockerignore:
```
node_modules
.git
*.md
.env
```
Observation:

Tells Docker what NOT to include when building an image.

Makes images smaller and builds faster.

Keeps secrets or unnecessary files out of the container.

## Task 6 – Build Optimization

Observation:

Docker builds images in layers.

If a layer hasn’t changed, Docker uses cache, which speeds up builds.

Stable things (like installing packages) go first.

Frequently changing things (like source code) go last.

Understanding layer order helps save time and space.





## Overall Observation:

Learned how to build, run, and optimize Docker images.

Practiced sending files into containers, running apps, and managing ports.

Learned how to structure projects to avoid confusion between multiple Dockerfiles.
