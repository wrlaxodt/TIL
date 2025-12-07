# Server Docker Container

## With Docker Hub

### Pull & Run Docker Images from Docker Hub

```bash
docker search <OPTIONS>     # Search Docker Hub for images
docker pull <OPTIONS>     # Pull Docker images from Docker Hub
docker run -it -d -p 8001:80 --name <server_name> <image_name>      # Run Docker images (-d: run in background)
```

### Edit Server Docker Container

#### 1. Connect to Docker

```bash
curl localhost:8001     # Check html
docker exec -it <container_name> bash     # Connect to Docker by bash (container must be running state)
cd /usr/share/nginx/html/
cat index.html
echo "fastcampus' nginx server!" > index.html     # Edit index.html
exit
```

#### 2. Copy index.html from Local to Docker Container

```bash
vi index.html     # Edit index.html
docker cp index.html <servername>:/usr/share/nginx/html/index.html     # Copy index.html to server
```

# Scikit-Learn Docker

## Set Docker Image

```bash
mkdir scikitlearn_docker
cd scikitlearn_docker
vi Dockerfile
```

```bash
FROM python:3.8-slim

WORKDIR /app

COPY requirements.txt /app/
RUN pip install --no-cache-dir -r requirements.txt

COPY model_learn.py /app/

CMD ["python", "./model_learn.py"]
```

```bash
vi requirements.txt
```

```bash
scikit-learn
pandas
numpy
```

```bash
vi model_learn.py
```

```python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import classification_report

# 데이터 셋 로드
data_url = "https://archive.ics.uci.edu/ml/machine-learning-databases/iris/iris.data"
columns = ['sepal_length', 'sepal_width', 'petal_length', 'petal_width', 'class']

data = pd.read_csv(data_url, names=columns)
print(data.head())

# 데이터 전 처리
X = data.drop('class', axis=1)
y = data['class']

# 훈련 및 테스트 데이터 분할
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)

# 모델 학습
model = RandomForestClassifier(n_estimators=100)
model.fit(X_train, y_train)

# 모델 평가
predictions = model.predict(X_test)
print(classification_report(y_test, predictions))
```

## Build Docker image

```bash
docker build -t scikitlearn_modellearn .     # Build docker image
docker images
docker run --name mldevelopment scikitlearn_modellearn     # Run docker image by mldevelopment
```

## Save Docker image to Docker Hub

```bash
docker tag <image_name> <dockerhub_username>/<image_name>:<tag>
docker push <dockerhub_username>/<image_name>:<tag>     # Push to Docker Hub Repository
```

## Download from Docker Hub Repository

```bash
docker stop <container_name>
docker rm <container_name>
docker rmi <dockerhub_username>/<image_name>:<tag> -f
docker pull <dockerhub_username>/<image_name>:<tag>     # Write it yourself or You can copy it from Docker Hub Repository
docker run --name <container_name> <dockerhub_username>/<image_name>:<tag>
```
