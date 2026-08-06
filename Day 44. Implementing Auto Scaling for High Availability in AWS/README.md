<!-- NAV_START -->
[⬅️ Back to Main README](../README.md) | [◀️ Previous Day](../Day%2043.%20Scaling%20and%20Managing%20Kubernetes%20Clusters%20with%20Amazon%20EKS) | [Next Day ▶️](../Day%2045.%20Configure%20NAT%20Gateway%20for%20Internet%20Access%20in%20a%20Private%20VPC)
<!-- NAV_END -->

Step 1: Create Security Group for EC2 & ALB

Go to EC2 → Security Groups

Click Create security group

Configuration

Security group name: `xfusion-sg`

VPC: Default VPC

Inbound Rules

Add:

Type: HTTP
Port: 80
Source: 0.0.0.0/0


Leave outbound rules as default

Click Create security group

Step 2: Create EC2 Launch Template

Go to EC2 → Launch Templates

Click Create launch template

Basic Details

Launch template name:

`xfusion-launch-template`

AMI & Instance Type

AMI: Amazon Linux 2

Instance type: t2.micro

Network & Security

Security group: xfusion-sg

User Data (IMPORTANT)

Under Advanced details → User data, paste:
```
#!/bin/bash
dnf update -y
dnf install -y nginx
systemctl start nginx
systemctl enable nginx
```

Click Create launch template

✅ Launch template is ready

Step 3: Create Target Group

Go to EC2 → Target Groups

Click Create target group

Configuration

Target type: Instances

Target group name:

`xfusion-tg`


Protocol: HTTP

Port: 80

VPC: Default VPC

Health Check

Protocol: HTTP

Path: /

Click Create target group

Step 4: Create Application Load Balancer

Go to EC2 → Load Balancers

Click Create load balancer

Choose Application Load Balancer

Basic Configuration

Name:

`xfusion-alb`


Scheme: Internet-facing

IP address type: IPv4

Network Mapping

VPC: Default VPC

Subnets: Select at least two AZs

Security Group

Select `xfusion-sg`

Listener & Routing

Listener:

HTTP : 80


Forward to:

xfusion-tg


Click Create load balancer

Step 5: Create Auto Scaling Group

Go to EC2 → Auto Scaling Groups

Click Create Auto Scaling group

Step 5.1: Choose Launch Template

Launch template: xfusion-launch-template

Version: Latest

Click Next

Step 5.2: Network

VPC: Default VPC

Subnets: Same AZs as ALB

Click Next

Step 5.3: Load Balancing

Select Attach to an existing load balancer

Choose:

`xfusion-tg`


Enable ELB health checks

Click Next

Step 5.4: Group Size & Scaling

Minimum capacity: 1

Desired capacity: 1

Maximum capacity: 2

Step 5.5: Scaling Policy

Select Target tracking scaling policy

Metric: Average CPU utilization

Target value:

50


Click Next → Create Auto Scaling group

✅ ASG is now active

Step 6: Verify Health Checks

Go to EC2 → Target Groups → `xfusion-tg`

Open Targets tab

Status should be:

Healthy

Step 7: Verify Application Access via ALB

Go to EC2 → Load Balancers

Select `xfusion-alb`

Copy DNS name

Open browser:

http://<ALB-DNS-NAME>

---

<!-- NAV_START -->
[⬅️ Back to Main README](../README.md) | [◀️ Previous Day](../Day%2043.%20Scaling%20and%20Managing%20Kubernetes%20Clusters%20with%20Amazon%20EKS) | [Next Day ▶️](../Day%2045.%20Configure%20NAT%20Gateway%20for%20Internet%20Access%20in%20a%20Private%20VPC)
<!-- NAV_END -->
