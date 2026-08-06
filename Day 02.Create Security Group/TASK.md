

The Nautilus DevOps team is strategizing the migration of a portion of their infrastructure to the AWS cloud. Recognizing the scale of this undertaking, they have opted to approach the migration in incremental steps rather than as a single massive transition. To achieve this, they have segmented large tasks into smaller, more manageable units. This granular approach enables the team to execute the migration in gradual phases, ensuring smoother implementation and minimizing disruption to ongoing operations. By breaking down the migration into smaller tasks, the Nautilus DevOps team can systematically progress through each stage, allowing for better control, risk mitigation, and optimization of resources throughout the migration process.

For this task, create a security group under default VPC with the following requirements:

Name of the security group is nautilus-sg.

The description must be Security group for Nautilus App Servers

Add the inbound rule of type HTTP, with port range of 80. Enter the source CIDR range of 0.0.0.0/0.

Add another inbound rule of type SSH, with port range of 22. Enter the source CIDR range of 0.0.0.0/0.



Use below given AWS Credentials: (You can run the showcreds command on aws-client host to retrieve these credentials)
Console URL 	https://415282657320.signin.aws.amazon.com/console?region=us-east-1
Username 	kk_labs_user_173003
Password 	YDAp^9u0@kA9
Start Time 	Tue Dec 02 13:12:26 UTC 2025
End Time 	Tue Dec 02 14:12:26 UTC 2025


Notes:

    Create the resources only in us-east-1 region.

    To display or hide the terminal of the AWS client machine, you can use the expand toggle button as shown below:
    toggle button

