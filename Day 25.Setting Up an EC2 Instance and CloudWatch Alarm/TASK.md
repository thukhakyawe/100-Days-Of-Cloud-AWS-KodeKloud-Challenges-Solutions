The Nautilus DevOps team has been tasked with setting up an EC2 instance for their application. To ensure the application performs optimally, they also need to create a CloudWatch alarm to monitor the instance's CPU utilization. The alarm should trigger if the CPU utilization exceeds 90% for one consecutive 5-minute period. To send notifications, use the SNS topic named datacenter-sns-topic which is already created.

    Launch EC2 Instance: Create an EC2 instance named datacenter-ec2 using any appropriate Ubuntu AMI.

    Create CloudWatch Alarm: Create a CloudWatch alarm named datacenter-alarm with the following specifications:
        Statistic: Average
        Metric: CPU Utilization
        Threshold: >= 90% for 1 consecutive 5-minute period.
        Alarm Actions: Send a notification to datacenter-sns-topic.
