### Dockerizer web-app(React-Node-Mongo) <ins>with docker-compose</ins>

Refer to the **docker-compose.yalm** file to view the configuration of each service (mongo, backend, frontend).

#### <p> Start all services:<p>

        docker-compose up -d

#### Stop all services:

        docker-compose down

#### Options:

#### Force the images to rebuild before starting the services:

        docker-compose up --build -d

#### Remove all volumes when services are stopped (except for anonymous volumes):

        docker-compose down -v

#### Start a specific service:

        docker-compose run service_name

#### Build a specific service and override the default command in the Dockerfile:

        docker-compose run service_name override_command

#### Execute a command when the service is starting:

        docker-compose exec command
