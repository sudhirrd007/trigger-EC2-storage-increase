# 1. Create IAM Role for Lambda

**REASON** - To give permission to lambda to modify storage of EC2 instance, we need to give lambda sufficient permissions

**Manual Creation**

* Name - sudhir-vm-lambda-iam
* give Permissions
  * AmazonEC2FullAccess
  * AmazonEBSCSIDriverPolicy
  * AWSLambda_FullAccess

# 2. Create Lambda

**REASON** - when alarm will trigger, it will send message to SNS. This SNS message will trigger this lambda as we are going to connect SNS and Lambda

**Manual Creation**

* Name - sudhir-vm-lambda

* select, Execution role - sudhir-vm-lambda-iam

* Add trigger

  * add SNS

* code

  ```python
  import boto3
  
  def lambda_handler(event, context):
      ec2 = boto3.client('ec2')
      
      # Modify the EBS volume size
      response = ec2.modify_volume(
          VolumeId='vol-0dff581451728a3a0',
          Size=10)
      
      print("====================== Volume Incresed =================================")
      
      return {
          'statusCode': 200,
          'body': json.dumps('Hello from Lambda!')
      }
  ```

  * VolumeId - go to EC2 instnace -> volume -> volumeId

* Deploy function