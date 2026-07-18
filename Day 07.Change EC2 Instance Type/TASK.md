During the migration process, the Nautilus DevOps team created several EC2 instances in different regions. They are currently in the process of identifying the correct resources and utilization and are making continuous changes to ensure optimal resource utilization. Recently, they discovered that one of the EC2 instances was underutilized, prompting them to decide to change the instance type. Please make sure the Status check is completed (if its still in Initializing state) before making any changes to the instance.

1) Change the instance type from t2.micro to t2.nano for nautilus-ec2 instance.

2) Make sure the ec2 instance nautilus-ec2 is in running state after the change.


Use below given AWS Credentials: (You can run the showcreds command on aws-client host to retrieve these credentials)
Console URL 	https://542759516395.signin.aws.amazon.com/console?region=us-east-1
Username 	kk_labs_user_838844
Password 	Wa!cM03eUBAS
Start Time 	Sat Dec 06 10:17:30 UTC 2025
End Time 	Sat Dec 06 11:17:30 UTC 2025