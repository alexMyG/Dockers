# Collection of docker compose templates

### Template 1: Docker jupyterlab GPU


You need a ".env" file with the following content:

```
JUPYTER_PASSWORD="YOUR JUPYTERLAB PASSWORD"
CONTAINER_NAME="YOUR CONTAINER'S NAME"
JUPYTERLAB_PORT="JUPTERLAB PORT"
```

### Template 2: Docker jupyterlab no GPU


You need a ".env" file with the following content:

```
JUPYTER_PASSWORD="YOUR JUPYTERLAB PASSWORD"
CONTAINER_NAME="YOUR CONTAINER'S NAME"
JUPYTERLAB_PORT="JUPTERLAB PORT"
```


### Template 2: Docker jupyterlab GPU + mongoDB

You need a ".env" file with the following content:

```
COMPOSE_PROJECT_NAME="YOUR PROJECT NAME"

MONGO_USER="USERNAME MONGO DB"
MONGO_PASSWORD="PASSWD MONGO DB"
MONGO_ACCESS_URL="MONGO URL WITH USERNAME AND PASSWORD"

JUPYTER_PASSWORD="JUPYTERLAB PASSWORD"

JUPYTERLAB_CONTAINER_NAME="A NAME FOR THE JUPYTERLAB CONTAINER"
JUPYTERLAB_PORT="OPEN PORT FOR JUPYTERLAB"

MONGO_CONTAINER_NAME="A NAME FOR THE MONGO DB CONTAINER"
MONGODB_PORT="OPEN PORT FOR MONGO DB"
```

## Starting docker-compose

```
UID=${UID} GID=${GID} USER=${USER} docker-compose --env-file .env up -d
```

- If you make any changes in the Jupterlab Dockerfile, then rebuild that service:

```
UID=${UID} GID=${GID} USER=${USER} docker-compose --env-file .env up -d --build
```

You can avoid passing UID, GID and USER by assigning your account's values into the env file


> :warning: **These images are prepared to create a user in the container that matches the host user.**: This avoids files permissions problems but the image is built including the UID, GID and USER variables of the host user. This means that future instances of the same image will inherit the data of the user that built the image. To avoid that, you should use new project and image names.
> If you need to rebuild the image completely, then run:

```docker-compose --env-file .env build --no-cache```
