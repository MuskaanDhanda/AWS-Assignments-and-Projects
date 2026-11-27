# Module 4: ELB and Route 53

> **Original Word document:** [Module 4 - ELB + Route 53.docx](Module%204%20-%20ELB%20%2B%20Route%2053.docx)

## Contents

- [Problem Statement](#problem-statement)
- [Task 1: Manage scaling requirements](#task-1-manage-scaling-requirements)
- [Task 2: Create a load balancer](#task-2-create-a-load-balancer)
- [Task 3: Route traffic to the company's domain](#task-3-route-traffic-to-the-companys-domain)

---

## Problem Statement

You work for XYZ Corporation, which uses on-premises solutions and a limited number of systems. As requests to their application increase, the load also increases, so the corporation has to buy more systems almost regularly. To cut down on these expenses, they decided to move their infrastructure to AWS.

### Tasks

1. Manage the scaling requirements of the company by:
   - a. Deploying multiple compute resources on the cloud as soon as the load increases and CPU utilization exceeds 80%
   - b. Removing the resources when CPU utilization goes under 60%
2. Create a load balancer to distribute the load between compute resources.
3. Route the traffic to the company's domain.

---

## Task 1: Manage scaling requirements

### a. Scale out when CPU utilization exceeds 80%

**Flow:**

```text
EC2 → AMI → Launch Template (associate AMI with template) → Auto Scaling Group → Target Group → Elastic Load Balancer
```

![Screenshot 01](images/01.png)

![Screenshot 02](images/02.png)

![Screenshot 03](images/03.png)

![Screenshot 04](images/04.png)

![Screenshot 05](images/05.png)

![Screenshot 06](images/06.png)

![Screenshot 07](images/07.png)

![Screenshot 08](images/08.png)

![Screenshot 09](images/09.png)

![Screenshot 10](images/10.png)

![Screenshot 11](images/11.png)

![Screenshot 12](images/12.png)

The Auto Scaling group launched **3 EC2 instances** on its own.

![Screenshot 13](images/13.png)

![Screenshot 14](images/14.png)

![Screenshot 15](images/15.png)

![Screenshot 16](images/16.png)

![Screenshot 17](images/17.png)

![Screenshot 18](images/18.png)

**Auto Scaling groups → select `musku-scaling` → Actions → Edit**, then add the target group associated with the load balancer.

![Screenshot 19](images/19.png)

![Screenshot 20](images/20.png)

![Screenshot 21](images/21.png)

![Screenshot 22](images/22.png)

![Screenshot 23](images/23.png)

![Screenshot 24](images/24.png)

**Create CloudWatch alarm → Metrics → Browse → EC2 → By Auto Scaling Group → select CPUUtilization for `musku-scaling` → Add → set parameters**

![Screenshot 25](images/25.png)

![Screenshot 26](images/26.png)

![Screenshot 27](images/27.png)

### b. Scale in when CPU utilization goes under 60%

![Screenshot 28](images/28.png)

![Screenshot 29](images/29.png)

![Screenshot 30](images/30.png)

---

## Task 2: Create a load balancer

![Screenshot 31](images/31.png)

![Screenshot 32](images/32.png)

**User data script:**

```bash
#!/bin/bash
yum update -y
yum install -y httpd.x86_64
systemctl start httpd.service
systemctl enable httpd.service
echo "hello you are viewing my website from $(hostname -f)" > /var/www/html/index.html
```

![Screenshot 33](images/33.png)

Copy the **Public IPv4 address** and open it with `http://` in a new browser tab.

![Screenshot 34](images/34.png)

![Screenshot 35](images/35.png)

Create a **target group** that lets the load balancer connect to all instances on HTTP port **80**.

![Screenshot 36](images/36.png)

![Screenshot 37](images/37.png)

Click **Include as pending below**, then **Create target group**.

![Screenshot 38](images/38.png)

Create an **Application Load Balancer** and select the target group created above.

![Screenshot 39](images/39.png)

![Screenshot 40](images/40.png)

Paste the load balancer's **DNS name** in a new browser tab.

![Screenshot 41](images/41.png)

**Results:**

![Screenshot 42](images/42.png)

![Screenshot 43](images/43.png)

![Screenshot 44](images/44.png)

> **Result:** Each refresh is served by a different EC2 instance behind the same load balancer DNS name.

---

## Task 3: Route traffic to the company's domain

![Screenshot 45](images/45.png)

![Screenshot 46](images/46.png)

![Screenshot 47](images/47.png)

![Screenshot 48](images/48.png)

![Screenshot 49](images/49.png)

![Screenshot 50](images/50.png)
