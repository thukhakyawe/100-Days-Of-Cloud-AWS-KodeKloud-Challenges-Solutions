<!-- NAV_START -->
[⬅️ Back to Main README](../README.md) | [◀️ Previous Day](../Day%2039.%20Hosting%20a%20Static%20Website%20on%20AWS%20S3) | [Next Day ▶️](../Day%2041.%20Securing%20Data%20with%20AWS%20KMS)
<!-- NAV_END -->

Step 1: Verify Internet Gateway (IGW) for xfusion-vpc

Go to VPC → Internet Gateways

Check if an Internet Gateway exists and is attached to xfusion-vpc


Select the IGW → Actions → Attach to VPC

Choose:

xfusion-vpc

![alt text](image.png)

![alt text](image-1.png)

✅ VPC now has a path to the internet

Step 2: Verify Route Table Configuration

Go to VPC → Route Tables

Identify the route table associated with the public subnet of xfusion-ec2

Check Subnet associations

Open Routes tab

![alt text](image-2.png)


Ensure this route exists:

Destination: 0.0.0.0/0
Target: Internet Gateway (igw-xxxx)

IPlease delete and add as New routes

Add route:

Destination: 0.0.0.0/0

Target: Internet Gateway

Save changes

![alt text](image-3.png)


✅ Subnet is now public

Step 3: Verify Subnet Auto-Assign Public IP

Go to VPC → Subnets

Select the subnet where xfusion-ec2 is running

Click Edit subnet settings

Ensure:

Enable auto-assign public IPv4 address ✔


Save

⚠️ If disabled, new instances won’t get public IPs automatically

![alt text](image-4.png)

Step 4: Verify EC2 Has a Public IP

Go to EC2 → Instances

Select xfusion-ec2

Check:

Public IPv4 address






Step 5: Final Internet Access Test

Open browser

Visit:

http://<EC2_PUBLIC_IP>


✅ You should now see the Nginx Welcome Page

✅ Issue Resolved – Root Cause Identified

---

<!-- NAV_START -->
[⬅️ Back to Main README](../README.md) | [◀️ Previous Day](../Day%2039.%20Hosting%20a%20Static%20Website%20on%20AWS%20S3) | [Next Day ▶️](../Day%2041.%20Securing%20Data%20with%20AWS%20KMS)
<!-- NAV_END -->
