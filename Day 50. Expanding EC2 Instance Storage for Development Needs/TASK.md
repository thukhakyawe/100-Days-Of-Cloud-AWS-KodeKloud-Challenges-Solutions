The Nautilus DevOps Team has recently been informed by the Development Team that their EC2 instance is running out of storage space. This instance, crucial for development activities, is named xfusion-ec2 and currently has an attached volume of 8 GiB. To accommodate the increasing data requirements, the storage needs to be expanded to 12 GiB. This change should ensure that the expanded space is immediately available for use within the instance without disrupting ongoing activities.

Identify Volume: Find the volume attached to the xfusion-ec2 instance.

Expand Volume: Increase the volume size from 8 GiB to 12 GiB.

Reflect Changes: Ensure the root (/) partition within the instance reflects the expanded size from 8 GiB to 12 GiB.

SSH Access: Use the key pair located at /root/xfusion-keypair.pem on the aws-client host to SSH into the EC2 instance.