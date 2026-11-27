# Module 3: IAM and CloudWatch

> **Original Word document:** [Module3-IAM +CloudWatch.docx](Module3-IAM%20%2BCloudWatch.docx)

## Contents

- [IAM Users Assignment](#iam-users-assignment)
- [IAM Roles Assignment](#iam-roles-assignment)
- [IAM Policies Assignment](#iam-policies-assignment)
- [CloudWatch Dashboard Assignment](#cloudwatch-dashboard-assignment)
- [CloudWatch Alarms Assignment](#cloudwatch-alarms-assignment)

> **Problem statement (all IAM and CloudWatch assignments):** You work for XYZ Corporation. To maintain the security of the AWS account and the resources, you have been asked to implement a solution that can help easily recognize and monitor the different users. The CloudWatch assignments also monitor the machines created by these users for any errors or misconfigurations.

---

## IAM Users Assignment

### Task 1: Create 4 IAM users named "Dev1", "Dev2", "Test1" and "Test2"

![Screenshot 01](images/01.png)

### Task 2: Create 2 groups named "Dev Team" and "Ops Team"

![Screenshot 02](images/02.png)

### Task 3: Add Dev1 and Dev2 to the Dev Team

![Screenshot 03](images/03.png)

### Task 4: Add Dev1, Test1 and Test2 to the Ops Team

![Screenshot 04](images/04.png)

---

## IAM Roles Assignment

### Task 1: Create a role that lets only user1 and user2 from task 1 have complete access to VPCs and DynamoDB

![Screenshot 05](images/05.png)

![Screenshot 06](images/06.png)

![Screenshot 07](images/07.png)

### Task 2: Log in as user1 and switch to the role to test it

![Screenshot 08](images/08.png)

> **Result:** Able to access VPC and DynamoDB through the role **dyna-vpc-role**.

---

## IAM Policies Assignment

### Task 1: Create policy number1, which lets users:

![Screenshot 09](images/09.png)

**a. Access S3 completely**

![Screenshot 10](images/10.png)

**b. Only create EC2 instances**

![Screenshot 11](images/11.png)

**c. Full access to RDS**

![Screenshot 12](images/12.png)

### Task 2: Create policy number2, which allows users to:

![Screenshot 13](images/13.png)

**a. Access CloudWatch and billing completely**

![Screenshot 14](images/14.png)

**b. Only list EC2 and S3 resources**

![Screenshot 15](images/15.png)

### Task 3: Attach policy number1 to the Dev Team from task 1

![Screenshot 16](images/16.png)

![Screenshot 17](images/17.png)

![Screenshot 18](images/18.png)

### Task 4: Attach policy number2 to the Ops Team from task 1

![Screenshot 19](images/19.png)

![Screenshot 20](images/20.png)

![Screenshot 21](images/21.png)

---

## CloudWatch Dashboard Assignment

### Task 1: Create a dashboard to check CPU utilization and networking for a particular EC2 instance

![Screenshot 22](images/22.png)

![Screenshot 23](images/23.png)

![Screenshot 24](images/24.png)

![Screenshot 25](images/25.png)

![Screenshot 26](images/26.png)

Similarly, click **+** at the top right to add a widget for **NetworkIn** and **NetworkOut**.

![Screenshot 27](images/27.png)

![Screenshot 28](images/28.png)

Click **Save**.

---

## CloudWatch Alarms Assignment

### Task 1: Create a billing alarm that goes off when estimated charges go above $500

**a. Enable billing preferences**

![Screenshot 29](images/29.png)

**b. Configure the alarm**

![Screenshot 30](images/30.png)

![Screenshot 31](images/31.png)

![Screenshot 32](images/32.png)

![Screenshot 33](images/33.png)

![Screenshot 34](images/34.png)

![Screenshot 35](images/35.png)

![Screenshot 36](images/36.png)

Alarm condition: **EstimatedCharges > 500 for 1 datapoint within 6 hours**.

### Task 2: Create an alarm that goes into the Alarm state when an EC2 instance's CPU utilization goes above 65%, with an SNS topic to notify the person

**a. Define the metric and threshold**

**Create alarm → Select metric → Browse: All → EC2 → Per-Instance Metrics**

![Screenshot 37](images/37.png)

![Screenshot 38](images/38.png)

![Screenshot 39](images/39.png)

**b. Configure actions and SNS notifications**

![Screenshot 40](images/40.png)

![Screenshot 41](images/41.png)

![Screenshot 42](images/42.png)

![Screenshot 43](images/43.png)
