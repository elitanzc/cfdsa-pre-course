## Building Docker image locally
To build image locally:
```bash
DOCKER_REPO="elitanzc"
IMAGE_TAG="cfdsa-dov-bear"
VERSION="v1"
docker build -t ${DOCKER_REPO}/${IMAGE_TAG}:${VERSION} .
```

Push to Docker Hub:
```bash
docker push ${DOCKER_REPO}/${IMAGE_TAG}:${VERSION}
```

## Pulling image from Docker Hub and running it
Pull image from Docker:
```bash
docker pull ${DOCKER_REPO}/${IMAGE_TAG}:${VERSION} 
```

Run image on image port 5000 instead of default 3000:
```bash
LOCAL_PORT=8000
docker run -d -p ${LOCAL_PORT}:5000 -e PORT=5000 ${DOCKER_REPO}/${IMAGE_TAG}:${VERSION} 
```

App can now be accessed from http://localhost:8000 :)