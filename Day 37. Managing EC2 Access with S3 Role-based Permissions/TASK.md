The Nautilus DevOps team needs to set up an application on an EC2 instance to interact with an S3 bucket for storing and retrieving data. To achieve this, the team must create a private S3 bucket, set appropriate IAM policies and roles, and test the application functionality.

Task:
1) EC2 Instance Setup:

An instance named xfusion-ec2 already exists.
The instance requires access to an S3 bucket.
2) Setup SSH Keys:

Create new SSH key pair (id_rsa and id_rsa.pub) on the aws-client host and add the public key to the root user's authorized keys on the EC2 instance.
3) Create a Private S3 Bucket:

Name the bucket xfusion-s3-29734.
Ensure the bucket is private.
4) Create an IAM Policy and Role:

Create an IAM policy allowing s3:PutObject, s3:ListBucket and s3:GetObject access to xfusion-s3-29734.
Create an IAM role named xfusion-role.
Attach the policy to the IAM role.
Attach this role to the xfusion-ec2 instance.
5) Test the Access:

SSH into the EC2 instance and try to upload a file to xfusion-s3-29734 bucket using following command:
aws s3 cp <your-file> s3://xfusion-s3-29734/

Now run following command to list the upload file:
aws s3 ls s3://xfusion-s3-29734/

