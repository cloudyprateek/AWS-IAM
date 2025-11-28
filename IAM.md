#  IAM (Identity and Access Management)

IAM is a **global service** and completely **free**. IAM is a security service in AWS that helps us manage who can access our AWS account and what they are allowed to do.  
Basically, through IAM we can create users, groups, roles and attach permissions using policies.  
IAM is a global service and we don’t pay anything for using IAM.

AWS gives full access only to the root user, so IAM is used to safely share access inside our team without giving root credentials.

## **Authentication**
Authentication means verifying the identity of a person or service.  
Basically “**Who are you?**”

Example:  
- Logging in using username & password  
- Using access keys  
- MFA verification  

## **Authorization**
Authorization decides what actions a user is allowed to perform.  
Basically “**What can you do?**”

Example:  
- Start or stop EC2  
- Read/Write S3 bucket  
- Create or delete resources  

**Authentication = identity check**  
**Authorization = permission check**

Both are controlled by IAM.

---

##  What IAM Includes

### 1. IAM User
A user is simply an identity for a person who needs AWS access.  
Users get login password and (if needed) access keys.

### 2. IAM Group
A group is a collection of users.  
If we attach a policy to a group, every user inside gets the same permissions.

### 3. IAM Role
A role is used by AWS services like EC2, Lambda, or by external users.  
Roles don’t have passwords; they work with temporary credentials.

### 4. IAM Policies
Policies are JSON permission documents.  
Using a policy we decide what actions a user/group/role can perform.

---

##  Types of IAM Policies

### 1. AWS Managed Policy
These are pre-made policies created by AWS.  
They are easy to use and updated automatically by AWS.  
Example: `AmazonS3FullAccess`, `AmazonEC2ReadOnlyAccess`.

### 2. Customer Managed Policy
These are policies that we create by ourselves.  
Useful when we want very specific permissions like one bucket or one EC2 instance access.

### 3. Inline Policy
Inline policy is attached directly to one user/group/role.  
It is not reusable and gets deleted when that identity is deleted.

---

# How to Create Things in IAM (GUI Steps)

##  Create IAM User (Console Steps)
1. Login to AWS Console  
2. Open IAM  
3. Go to **Users** → **Create user**  
4. Enter username  
5. Select **Console access** or **Programmatic access**  
6. Set password  
7. Add permissions (group/policy)  
8. Create user  

##  Create IAM Group
1. IAM → **User groups**  
2. Click **Create group**  
3. Enter group name  
4. Attach policies  
5. Add users (optional)  
6. Create  

##  Create IAM Policy
1. IAM → **Policies**  
2. Create policy  
3. Use **Visual editor** or **JSON**  
4. Choose service → example: S3  
5. Select actions → List/Get/Put  
6. Select resources  
7. Give name → Create  

##  Create IAM Role
1. IAM → **Roles**  
2. Create role  
3. Choose AWS service (ex: EC2)  
4. Attach policies  
5. Give name  
6. Create role  

---

# JSON Policies (Simple Examples)

### Simple S3 ListBucket Permission
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:ListBucket",
      "Resource": "arn:aws:s3:::mybucket"
    }
  ]
}
