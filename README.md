# Collection of docker compose templates

### Jupyterlab


You need a ".env" file with the following content:

```
JUPYTER_PASSWORD="YOUR JUPYTERLAB PASSWORD"
CONTAINER_NAME="YOUR CONTAINER'S NAME"
JUPYTERLAB_PORT="JUPTERLAB PORT"
```


## Jupyterlab + MONGODB

You need a ".env" file with the following content:

```
COMPOSE_PROJECT_NAME="$$$$$$$$$$$$$$"

MONGO_USER="="$$$$$$$$$$$$$$""
MONGO_PASSWORD="="$$$$$$$$$$$$$$""
MONGO_ACCESS_URL="="$$$$$$$$$$$$$$""

JUPYTER_PASSWORD="$$$$$$$$$$$$$$"

JUPYTERLAB_CONTAINER_NAME="$$$$$$$$$$$$$$"
JUPYTERLAB_PORT="$$$$$$$$$$$$$$"

MONGO_CONTAINER_NAME="$$$$$$$$$$$$$$"
MONGODB_PORT="$$$$$$$$$$$$$$"
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


- If using a different UID/GID in the same machine and same image name, we need to rebuild with no cache

```
UID=${UID} GID=${GID} USER=${USER} docker-compose --env-file .env build --no-cache
```
