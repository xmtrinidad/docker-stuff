# Networking - (Cross-)Container Communication

* When using external APIs, they will work the same they do when working locally
* To connect to another server or DB locally, use ```host.docker.internal``` instead of *localhost*

## Example MongoDB connection

```javascript
mongoose.connect(
  'mongodb://host.docker.internal:27017/swfavorites',
  { useNewUrlParser: true },
  (err) => {
    if (err) {
      console.log(err);
    } else {
      app.listen(3000);
    }
  }
);
```

## Connecting to a containerized MongoDB Instance

* host.docker.internal won't work in this case
* Use docker inspect container-name to locate the IP of the container
* Replace localhost/host.docker.internal with the IP

## Another Solution - Networking

* docker network create favorites-net
* docker run --network my_network ...
  * MongoDB example:
  * docker run -d --name mongodb --network favorites-net mongo
* Once part of a network, rather than using the container IP or host.docker.internal, you can use the name of the container

```javascript
mongoose.connect(
  'mongodb://mongodb:27017/swfavorites',
  { useNewUrlParser: true },
  (err) => {
    if (err) {
      console.log(err);
    } else {
      app.listen(3000);
    }
  }
);
```

* docker run --name favorites -d --network favorites-net --rm -p 3000:3000 favorites-node