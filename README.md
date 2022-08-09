## Overview
A simple user-profile JavaScript Application to be implemented using Docker run command

### Tools
-   Docker
-   HTML, CSS
-   MongoDB, Mongo-Express data storage
-   Nodejs backend

#### Building the application
-   Pull the images for mongodb and mongo-express
```
docker pull mongodb
docker pull mongo-express:0.54.0
```
Reference:  [MongoDB](Readme.images/1.png), [Mongo-Express](/Readme.images/2.png)
-   Create docker network
```
    docker network create mongo-network 
```

-   Start mongodb inside docker container
```
    docker run -d \
    -p 27017:27017 \
    -e MONGO_INITDB_ROOT_USERNAME=admin \
    -e MONGO_INITDB_ROOT_PASSWORD=password \
    --net mongo-network \
    --name mongodb \
    mongo
```
Reference: [Docker Network & Mongo Docker run](/Readme.images/3.png)
- Start mongo-express inside docker container
```    
    docker run -d \
    -p 8081:8081 \
    -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin \
    -e ME_CONFIG_MONGODB_ADMINPASSWORD=password \
    --net mongo-network --name mongo-express \
    -e ME_CONFIG_MONGODB_SERVER=mongodb \
    mongo-express:0.54.0   
```
Reference: [Docker Run Mongo-Express](/Readme.images/4.png)
-   Open mongo-express from browser
```
    http://localhost:8081
```

-   Create `my-db` _db_ and `users` _collection_ in mongo-express dashboard.

    Reference: [my-db](/Readme.images/5.png), [users](/Readme.images/6.png)
- Start your nodejs application locally - go to `app` directory of project 
```
    npm install 
    node server.js
```
Reference: [npm install](/Readme.images/7.png), [node](/Readme.images/8.png)
- Access you nodejs application UI from browser

    http://localhost:3000

- Add a [user profile](/Readme.images/9.png) in application UI
- Go to [mongo-express dashboard](/Readme.images/10.png) and ensure addition of credentials
```
    http://localhost:8081
```
### Credits
Tech With Nana [GitLab](https://gitlab.com/nanuchi/techworld-js-docker-demo-app)