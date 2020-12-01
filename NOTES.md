Quick commands:

docker images
- List images

docker build .
- Build image using dockerfile in directory

docker run -p hostport:containerPort imageId
- Basic command for running node app on exposed port listed in dockerfile

docker ps
- list running processes

docker stop containerName
- stop container

---

Python related commands

docker run -it containerId
- run container in interactive mode

docker start -i -a customName
- start container in interactive and attached mode

---

docker run -it --name custom-name containerId
- Create custom container name

docker stop containerName
- stop container

docker ps -a
-  list all containers, including stopped

docker start containerName
-  start a container in detached mode

docker rm container_name
- Remove container

docker image prune -a
- Remove all images

docker build -t node-demo:latest .
- Example of tagging an image with custom name

docker run -p 8000:3000 -d --name nodeapp --rm node-demo:latest
- rm flag removes container automatically when it's stopped

---

## Sharing Images

Docker Hub and Private Registry

docker push IMAGE_NAME
docker pull IMAGE_NAME

## Volumes

docker run -d -p 3000:80 --rm --name feedback-app -v feedback:/app/feedback feedback-node:volumes
- container example with named volumes

docker volume rm VOL_NAME
docker volume prune
- remove docker volumes

### Bind mounts example

docker run -d -p 3000:80 --rm --name feedback-app -v feedback:/app/feedback - 
v "%cd%":/app feedback-node:volumes

### Using ananoymous volume for node_modules

docker run -d -p 3000:80 --rm --name feedback-app -v feedback:/app/feedback -v ${pwd}:/app -v /app/node_modules feedback-node:volumes

**Note**    
There's a weird thing with git bash and th above command will not work.  I used powershell to get it to work.

**Nodemon note**

When using nodemon with docker for node.js apps, use the -L flag to detect changes

```json
 "scripts": {
    "start": "nodemon -L server.js"
  }
  ```