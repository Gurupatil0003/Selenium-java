# AWS S3 File Upload Using Python (Boto3)

## Goal

Upload a file from your local machine to an AWS S3 bucket using Python
and generate a public download URL.

``` text
Local File
     ↓
Python Program
     ↓
Boto3 SDK
     ↓
AWS IAM Authentication
     ↓
AWS S3 Bucket
     ↓
Public Download URL
```

------------------------------------------------------------------------

# Prerequisites

-   AWS Account
-   S3 Bucket
-   IAM User with S3 permissions
-   Python installed

# Step 1: Create an S3 Bucket

1.  Login to AWS Console.
2.  Open **S3**.
3.  Click **Create Bucket**.
4.  Select **General Purpose** bucket.
5.  Enter a unique bucket name (example: `dddd-dd`).
6.  Disable **Block all public access** (for testing only).
7.  Create the bucket.

# Step 2: Configure Public Download Access

Go to:

`S3 -> Bucket -> Permissions -> Bucket Policy`

Add:

``` json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicRead",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::dddd-dd/*"
    }
  ]
}
```

# Step 3: Create IAM User

Go to:

`IAM -> Users -> Create User`

Example username:

`Guru`

# Step 4: Attach Permissions

Select:

`Attach policies directly`

Attach:

`AmazonS3FullAccess`

# Step 5: Create Access Keys

Go to:

`IAM -> Users -> Guru -> Security Credentials -> Access Keys -> Create Access Key`

Choose:

`Local Code`

Save:

-   Access Key ID
-   Secret Access Key

# Step 6: Install Boto3

``` bash
pip install boto3
```

# Step 7: Project Structure

``` text
project/
├── upload.py
└── dog_PNG50396.png
```

# Step 8: Python Upload Code

``` python
import boto3

ACCESS_KEY = "YOUR_ACCESS_KEY"
SECRET_KEY = "YOUR_SECRET_KEY"

s3 = boto3.client(
    "s3",
    aws_access_key_id=ACCESS_KEY,
    aws_secret_access_key=SECRET_KEY,
    region_name="us-west-2"
)

local_file = "dog_PNG50396.png"
bucket_name = "dddd-dd"
s3_file_name = "dog.png"

s3.upload_file(
    local_file,
    bucket_name,
    s3_file_name
)

print("Upload Successful!")

url = f"https://{bucket_name}.s3.us-west-2.amazonaws.com/{s3_file_name}"
print(url)
```

# Step 9: Run

``` bash
python upload.py
```

# Common Error

If you get:

``` text
AccessDenied: User is not authorized to perform s3:PutObject
```

Go to:

`IAM -> Users -> Guru -> Permissions`

and attach:

`AmazonS3FullAccess`

# Architecture

``` text
Local Computer
      ↓
Python Script
      ↓
Boto3
      ↓
IAM Credentials
      ↓
AWS S3
      ↓
Public URL
```
