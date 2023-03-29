# Download and Configure Cloud Watch Agent

**REASON** - We can have different metrics using cloud watch metrics. But we can only use pre-defined metrics from cloud watch. In this case study we want to know storage utilization in %, which is not provided by cloud watch. So, in this case, in our EC2 we can install cloud watch agent, which can send custom metrics to our cloud watch.

**Follow all below command in EC2's console**

**1. Download**

*  refer this link - [Download and configure the CloudWatch agent using the command line - Amazon CloudWatch](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/download-cloudwatch-agent-commandline.html)`

  ```shell
  wget https://s3.amazonaws.com/amazoncloudwatch-agent/ubuntu/arm64/latest/amazon-cloudwatch-agent.deb
  
  sudo dpkg -i -E ./amazon-cloudwatch-agent.deb
  ```

**2. amazon-cloudwatch-agent-config-wizard**

```shell
sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-config-wizard
```

* answer all the prompts

**3. Run Cloud Watch Agent**

```shell
sudo  /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl -a fetch-config -m ec2 -c file:/opt/aws/amazon-cloudwatch-agent/bin/config.json -s
```

