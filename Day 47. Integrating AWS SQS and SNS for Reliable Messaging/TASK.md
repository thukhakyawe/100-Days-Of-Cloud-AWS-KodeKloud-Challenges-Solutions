

The Nautilus DevOps team needs to implement priority queuing using Amazon SQS and SNS. The goal is to create a system where messages with different priorities are handled accordingly. You are required to use AWS CloudFormation to deploy the necessary resources in your AWS account. The CloudFormation template should be created on the AWS client host at /root/nautilus-priority-stack.yml, the stack name must be nautilus-priority-stack and it should create the following resources:

    Two SQS queues named nautilus-High-Priority-Queue and nautilus-Low-Priority-Queue.
    An SNS topic named nautilus-Priority-Queues-Topic.
    A Lambda function named nautilus-priorities-queue-function that will consume messages from the SQS queues. The Lambda function code is provided in /root/index.py on the AWS client host.
    An IAM role named lambda_execution_role that provides the necessary permissions for the Lambda function to interact with SQS and SNS.

Once the stack is deployed, to test the same you can publish messages to the SNS topic, invoke the Lambda function and observe the order in which they are processed by the Lambda function. The high-priority message must be processed first.

```
topicarn=$(aws sns list-topics --query "Topics[?contains(TopicArn, 'nautilus-Priority-Queues-Topic')].TopicArn" --output text)

aws sns publish --topic-arn $topicarn --message 'High Priority message 1' --message-attributes '{"priority" : { "DataType":"String", "StringValue":"high"}}'

aws sns publish --topic-arn $topicarn --message 'High Priority message 2' --message-attributes '{"priority" : { "DataType":"String", "StringValue":"high"}}'

aws sns publish --topic-arn $topicarn --message 'Low Priority message 1' --message-attributes '{"priority" : { "DataType":"String", "StringValue":"low"}}'

aws sns publish --topic-arn $topicarn --message 'Low Priority message 2' --message-attributes '{"priority" : { "DataType":"String", "StringValue":"low"}}'
```