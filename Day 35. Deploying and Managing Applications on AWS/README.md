<!-- NAV_START -->
[⬅️ Back to Main README](../README.md) | [◀️ Previous Day](../Day%2034.%20Create%20a%20Lambda%20Function%20Using%20CLI) | [Next Day ▶️](../Day%2036.%20Load%20Balancing%20EC2%20Instances%20with%20Application%20Load%20Balancer)
<!-- NAV_END -->

Step 1: Create a Private RDS MySQL Instance

Log in to the AWS Management Console.

Navigate to RDS → Databases → Create database.

Select Full configuration.

Engine Configuration

Engine type: MySQL

Version: MySQL 8.4.5

Template

Choose Sandbox template[Dev/Test].

Settings

DB instance identifier:

datacenter-rds


Master username:

datacenter_admin


Master password:

Set a strong password and note it (you’ll need it later).

Instance Configuration

DB instance class:

db.t3.micro

Storage

Storage type: gp2

Allocated storage: 5 GiB

Connectivity

Select Do NOT enable Public Access (private RDS).

Use the default VPC (sandbox).

Choose the same VPC as datacenter-ec2.

Create New SG

Additional Configuration

Initial database name:

datacenter_db


Leave all other options default.

Click Create database.

Wait until the RDS status shows Available.

Step 2: Configure Security Groups

Create New SG for EC2 . Allow SSH, HTTP from anywhere.

Edit DB's SG. Add 3306 from EC's SG

Note - lab use default SG for EC2 and RDS but need to add ssh,http from anywhere.

Step 3: Connect to datacenter-ec2 and Configure SSH Access
Create SSH Key on aws-client

Connect to the aws-client host.

Run:
```
ssh-keygen -t rsa -f /root/.ssh/id_rsa -N ""
```
Copy Public Key to datacenter-ec2

Connect to datacenter-ec2 via AWS Console (EC2 Instance Connect).

Edit authorized keys:
```
sudo -i
cd .ssh
vi authorized_keys
```



Paste contents of:

/root/.ssh/id_rsa.pub


Save and exit.

Verify Password-less SSH

From aws-client:
```
ssh root@34.229.17.51
```
Step 4: Copy index.php and Configure RDS Connection
Copy File



From aws-client, run:
```
scp /root/index.php root@34.229.17.51:/var/www/html/
```
Edit index.php

SSH into datacenter-ec2.

Edit the file:
```
cd /var/wwww/html
rm -rf index.html 
vi /var/www/html/index.php
```

Update database values :
```
<?php
$dbname = 'datacenter_db';
$dbuser = 'datacenter_admin';
$dbpass = 'K9ccs9jfgVxv6SEk1aZR';
$dbhost = 'datacenter-rds.cikalrhqc5jv.us-east-1.rds.amazonaws.com';

$link = mysqli_connect($dbhost, $dbuser, $dbpass) or die("Unable to Connect to '$dbhost'");
mysqli_select_db($link, $dbname) or die("Could not open the db '$dbname'");

$test_query = "SHOW TABLES FROM $dbname";
$result = mysqli_query($link, $test_query);

$tblCnt = 0;
while($tbl = mysqli_fetch_array($result)) {
  $tblCnt++;
}

if (!$tblCnt) {
  echo "Connected successfully<br />\n";
} else {
  echo "Connected successfully<br />\n";
}
?>
```
   


Save and exit.

Step 5: Validate the Setup
```      
curl local host
```

✅ You should see: Connected successfully<br />

---

<!-- NAV_START -->
[⬅️ Back to Main README](../README.md) | [◀️ Previous Day](../Day%2034.%20Create%20a%20Lambda%20Function%20Using%20CLI) | [Next Day ▶️](../Day%2036.%20Load%20Balancing%20EC2%20Instances%20with%20Application%20Load%20Balancer)
<!-- NAV_END -->
