# Docker

## How to start

### Make Directory

```bash
mkdir practice_hellodockerworld
```

### Create Dockerfile

```dockerfile
FROM python:3.8-slim
WORKDIR /app
COPY main.py /app
CMD ["python", "main.py"]
```

### Create main.py

```python
print("Hello, Docker World!")
```

### Build Docker Image

```bash
docker build -t hello-docker-world .
```

### Check & Remove Docker Images

```bash
docker images               # list images
docker rmi hello-docker-world
docker rmi hello-docker-world -f
docker rmi <IMAGE_ID>       # remove <none> image
```

### Run Docker Container

```bash
docker run hello-docker-world
```

### Check & Stop Running Containers

```bash
docker ps                   # running containers
docker stop <CONTAINER_ID>
```
