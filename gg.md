# AWS IAM Hands-on Lab (User + Group + Policy)

## Objective

Learn to create an IAM User, Group, and Custom Policy and grant S3
access.

## Steps

### 1. Create an S3 Bucket

Bucket name: `guru-demo-bucket`

### 2. Create an IAM User

IAM → Users → Create user

Username: `guru`

### 3. Create an IAM Group

IAM → User groups → Create group

Group: `Developers`

### 4. Add User to Group

Add user `guru` to `Developers`.

### 5. Create a Custom Policy

IAM → Policies → Create policy → JSON

``` json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:ListAllMyBuckets",
        "s3:GetBucketLocation"
      ],
      "Resource": "*"
    }
  ]
}
```

Policy name: `MyS3Policy`

### 6. Attach Policy to Group

IAM → User groups → Developers → Permissions → Add permissions

Select `MyS3Policy`.

### 7. Login as IAM User

Sign out from root and log in as `guru`.

### 8. Verify

Open S3. The user can list buckets but cannot delete them.

## Flow

``` text
Custom Policy
      |
      v
Developers Group
      |
      v
IAM User (guru)
      |
      v
Amazon S3
```


```python

# Build image
docker build -t flask-demo .

# Create container
docker run -d -p 5000:5000 --name flask-container flask-demo

# Check
docker ps

# Stop
docker stop flask-container

# Remove container
docker rm flask-container

# Remove image
docker rmi flask-demo

```

```python
# app/main.py
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello_world():
 return 'Hello, World!'
if __name__ == '__main__':
 app.run(host='0.0.0.0', port=5000)


```

```python
Flask==2.2.5
Werkzeug==2.2.3

```

```python
#FROM eclipse-temurin:21-jdk
#
#WORKDIR app/
#
#COPY /src/main/java/gg.java .
#
#RUN javac gg.java
#
#CMD ["java","gg"]
#
#
#

# Python base image
FROM python:3.9-slim

# Working directory inside container
WORKDIR /app

# Copy requirements
COPY src/main/java/requirements.txt .

# Install dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy application code
COPY src/main/java/ .

# Run application
CMD ["python", "app.py"]



```

```python
