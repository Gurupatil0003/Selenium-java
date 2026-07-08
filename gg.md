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
