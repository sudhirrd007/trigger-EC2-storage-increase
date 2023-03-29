# Create and Configure Alarm

**REASON** - By using this alarm we can perform some actions when storage utilization crosses 80% threshold. Cloud Watch agent keep sending metrics to cloud watch. Here, we will set an alarm, which will trigger after crossing of 80% storage utilization.

**Manual Creation**

* Name - sudhir-vm-alarm

* In metrics section, there is an option like below

  ![image-20230329150813313](Screenshots/image-20230329150813313.png)

* This option was not available before, but now is available, because we have installed cloud watch agent into EC2 instance.

  * **WARNING** - Do not forgot to change the region to EC2's region 

* By clicking on it, we can see various metrics

* select metric as below

  ![image-20230329151656550](screenshots/2.png)

* Under Conditions
  * select Greater than 80%
* Under Notification
  * create a new SNS topic
  * Here, enter email address on which you want your alert to send