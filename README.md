## Dockerizer web-app(React-Node-Mongo) with multi-containers <ins>without docker-compose</ins>

### Network:

<p>Create a network for communication between backend and mongo container</p>

        docker network create webAppNet

### Mongo:

##### Build image:

        docker run mongo

##### RUN container:

        docker run --name mongodb --rm -d --network webAppNet -v mongodata:/data/db -e MONGO_INITDB_ROOT_USERNAME=corgi -e MONGO_INITDB_ROOT_PASSWORD=secret mongo

### Back:

##### Build image:

        docker build --tag backend-img .

##### RUN container:

        docker run --name nodeApp --rm -d -p 80:80 --network webAppNet -v logs:/app/logs -v /Users/lamtan/Documents/dev/git/docker-practice-multicontainer/backend:/app -v /app/node_modules -e MONGODB_USERNAME=corgi backend-img

### Front:

##### Build image:

        docker build --tag frontend-img .

##### RUN container:

        docker run --name reactApp --rm -it -p 3000:3000 -v /Users/lamtan/Documents/dev/git/docker-practice-multicontainer/frontend/src:/app/src frontend-img

**Absolute path of all bind volumes above must be modified depending on the machine**

    Ex:
        /Users/lamtan/Documents/dev/git/docker-practice-multicontainer/backend
        /Users/lamtan/Documents/dev/git/docker-practice-multicontainer/frontend/src

#### Note:

The version using <ins>docker-compose</ins> is on the branch <ins>with-docker-compose</ins>
