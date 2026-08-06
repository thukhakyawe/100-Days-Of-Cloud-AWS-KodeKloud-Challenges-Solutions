<!-- NAV_START -->
[⬅️ Back to Main README](../README.md) | [◀️ Previous Day](../Day%2033.%20Create%20a%20Lambda%20Function) | [Next Day ▶️](../Day%2035.%20Deploying%20and%20Managing%20Applications%20on%20AWS)
<!-- NAV_END -->

🔹 Step 1: Create the Python script

On the aws-client host, run:

```
cat << 'EOF' > lambda_function.py
def lambda_handler(event, context):
    return {
        "statusCode": 200,
        "body": "Welcome to KKE AWS Labs!"
    }
EOF
```


Verify the file:
```
cat lambda_function.py
```

🔹 Step 2: Zip the Python script
```
zip function.zip lambda_function.py

# Verify:

ls -l function.zip
```

🔹 Step 3: Get the IAM role ARN

You must use the existing role lambda_execution_role.

Run:
```
aws iam get-role \
  --role-name lambda_execution_role \
  --query "Role.Arn" \
  --output text
```

📌 Copy the ARN (you’ll use it in the next command).

🔹 Step 4: Create the Lambda function using the zip file


```
aws lambda create-function \
  --function-name xfusion-lambda-cli \
  --runtime python3.9 \
  --role arn:aws:iam::831788756997:role/lambda_execution_role \
  --handler lambda_function.lambda_handler \
  --zip-file fileb://function.zip
```

✅ If successful, AWS will return a JSON output with function details.

🔹 Step 5: Verify the Lambda function (optional but recommended)
Invoke the function:
```
aws lambda invoke \
  --function-name xfusion-lambda-cli \
  response.json
```

Check the response:

✅ Expected output:
{
  "statusCode": 200,
  "body": "Welcome to KKE AWS Labs!"
}

---

<!-- NAV_START -->
[⬅️ Back to Main README](../README.md) | [◀️ Previous Day](../Day%2033.%20Create%20a%20Lambda%20Function) | [Next Day ▶️](../Day%2035.%20Deploying%20and%20Managing%20Applications%20on%20AWS)
<!-- NAV_END -->
