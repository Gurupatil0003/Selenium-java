```python

<!DOCTYPE html>
<html>
<head>
    <title>My CI/CD App</title>
    <style>
        body {
            font-family: Arial;
            text-align: center;
            margin-top: 100px;
            background: #f4f4f4;
        }

        h1 {
            color: #563939;
        }

        .box {
            background: white;
            padding: 30px;
            margin: auto;
            width: 500px;
            border-radius: 10px;
        }
    </style>
</head>

<body>

<div class="box">
    <h1>🚀 CI/CD Application</h1>

    <p>Application is running inside Docker.</p>

    <p>CI/CD deployment successful!</p>
</div>

</body>
</html>

```


```python

FROM nginx:alpine

COPY index.html /usr/share/nginx/html/index.html

EXPOSE 80
```

```python
services:

  web:
    build: .
    container_name: cicd-app
    ports:
      - "8081:80"

```


```python

name: CI/CD Pipeline

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:

      - name: Checkout Code
        uses: actions/checkout@v4

      - name: Build Docker Image
        run: docker build -t my-cicd-app .

      - name: Run Docker Container
        run: docker run -d -p 8080:80 --name test-container my-cicd-app

      - name: Wait for Application
        run: sleep 5

      - name: Test Application
        run: curl --fail http://localhost:8080

      - name: Stop Container
        if: always()
        run: docker stop test-container

```


```python

docker compose up -d --build
docker ps

```

```python
git add .
git commit -m "Fix Docker application test"
git push

```
