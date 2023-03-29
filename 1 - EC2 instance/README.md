# 1. Create Security group for EC2 instance

**REASON** - we are creating this security group in first place, so while creating EC2 instance we can just attach this security rules to our VM.

**Manual Creation**

* Name - sudhir-vm-securitygroup

* for **inbound rules** define the following
  * HTTP, RDP and SSH
* for **outbound rules** define the following
  * all to all traffic

# 2. Create IAM Role

**REASON** - We need to give EC2 instance enough permissions

**Manual Creation**

* Name - sudhir-vm-iam

* give 2 permissions
  * CloudWatchAgentAdminPolicy
  * AmazonSSMFullAccess

# 3. Create Linux EC2 instance with 8 GB SSD

**Manual Creation**

- Name - sudhir-vm
- select "sudhir-vm-securitygroup" security group
- select "sudhir-vm-iam" iam role
- For storage select 8 GB