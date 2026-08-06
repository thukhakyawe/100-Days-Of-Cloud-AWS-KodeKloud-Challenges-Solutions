The Nautilus DevOps team continues to explore serverless architecture by setting up another Lambda function. This time, the task must be completed using the AWS Console to familiarize the team with the web interface. The function will return a custom greeting and demonstrate the capabilities of AWS Lambda effectively.

Create Python Script: Create a Python script named lambda_function.py with a function that returns the body Welcome to KKE AWS Labs! and status code 200.

Zip the Python Script: Zip the script into a file named function.zip.

Create Lambda Function: Create a Lambda function named xfusion-lambda-cli using the zipped file and specify Python as the runtime.

IAM Role: Use the IAM role named lambda_execution_role.

Use AWS CLI which is already configured on the aws-client host.