<!-- NAV_START -->
[⬅️ Back to Main README](../README.md) | [◀️ Previous Day](../Day%2019.Attach%20IAM%20Policy%20to%20IAM%20User) | [Next Day ▶️](../Day%2021.Setting%20Up%20an%20EC2%20Instance%20with%20an%20Elastic%20IP%20for%20Application%20Hosting)
<!-- NAV_END -->

#### Step-by-Step Instructions (AWS Console)
1. Log in to AWS Console

Use your lab credentials.

2. Open IAM Service

In the AWS search bar → type IAM

Click IAM

3. Create the IAM Role

In the left navigation pane → click Roles

Click Create role

4. Select Trusted Entity

On the Select trusted entity page:

Trusted entity type: AWS service

Use case: EC2

Click Next.

![alt text](image.png)

5. Attach Permissions Policy

In the permissions list, search for:

`iampolicy_mark`


Select the policy iampolicy_mark

Click Next

![alt text](image-1.png)

6. Name the Role

On the Name, review, and create page:

Role name: `iamrole_mark`

(Optional) Description:

IAM role for EC2 with iampolicy_mark attached


Click Create role.

![alt text](image-2.png)

---

<!-- NAV_START -->
[⬅️ Back to Main README](../README.md) | [◀️ Previous Day](../Day%2019.Attach%20IAM%20Policy%20to%20IAM%20User) | [Next Day ▶️](../Day%2021.Setting%20Up%20an%20EC2%20Instance%20with%20an%20Elastic%20IP%20for%20Application%20Hosting)
<!-- NAV_END -->
