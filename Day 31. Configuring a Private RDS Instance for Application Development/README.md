<!-- NAV_START -->
[⬅️ Back to Main README](../README.md) | [◀️ Previous Day](../Day%2030.%20Enable%20Internet%20Access%20for%20Private%20EC2%20using%20NAT%20Instance) | [Next Day ▶️](../Day%2032.%20Snapshot%20and%20Restoration%20of%20an%20RDS%20Instance)
<!-- NAV_END -->

🧭 STEP-BY-STEP SOLUTION (AWS Console)
🔹 Step 1: Open RDS Console

Go to AWS Console → RDS

Click Create database

🔹 Step 2: Choose Database Creation Method

Select Full Configuration

(Do not choose Easy create)

🔹 Step 3: Engine Configuration

Engine type: MySQL

Engine version: MySQL 8.4.x
(Choose the latest 8.4 option available)

✔ This satisfies the engine requirement.

🔹 Step 4: Templates

Select Sandbox
(I choose dev/test)

🔹 Step 5: DB Instance Settings

DB instance identifier:

nautilus-rds


Credentials:

Username: keep default (e.g., admin)

Password: auto-generate or set manually (either is fine for the lab)

🔹 Step 6: Instance Configuration

DB instance class:

db.t3.micro


✔ Free-tier eligible and required by lab.

🔹 Step 7: Storage Configuration

Keep default storage type

✅ Enable storage autoscaling

Maximum storage threshold:

50 GB


⚠️ This value is mandatory — do not skip it.

🔹 Step 8: Connectivity (PRIVATE is critical)

VPC: Default or existing (keep default)

Public access:
❌ No (must be private)

Subnet group: Default

Security group: Default (or existing)

✔ This ensures the RDS is private, as required.

🔹 Step 9: Additional Configuration

Leave all other settings as default

No backups / monitoring changes needed unless already enabled by template

🔹 Step 10: Create Database

Click Create database

⏳ WAIT FOR AVAILABILITY (VERY IMPORTANT)

Go to RDS → Databases

Select nautilus-rds

Wait until Status = Available

⏱ This may take 5–10 minutes

🚫 Do NOT submit while status is:

Creating

Modifying

Backing-up

---

<!-- NAV_START -->
[⬅️ Back to Main README](../README.md) | [◀️ Previous Day](../Day%2030.%20Enable%20Internet%20Access%20for%20Private%20EC2%20using%20NAT%20Instance) | [Next Day ▶️](../Day%2032.%20Snapshot%20and%20Restoration%20of%20an%20RDS%20Instance)
<!-- NAV_END -->
