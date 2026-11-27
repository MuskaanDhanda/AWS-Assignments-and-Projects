# Module 2: EC2, EBS and EFS

> **Original Word document:** [Module 2-EC2+EBS+EFS.docx](Module%202-EC2%2BEBS%2BEFS.docx)

## Contents

- [Assignment: EC2 and EFS](#assignment-ec2-and-efs)
- [Case Study 1: Web Servers with AMI and EBS](#case-study-1-web-servers-with-ami-and-ebs)

---

## Assignment: EC2 and EFS

### Task

1. Create an EFS and connect it to 3 different EC2 instances. Make sure that all instances have different operating systems, for example Ubuntu, Red Hat Linux and Amazon Linux 2.

### Solution

#### Step 1: Create the EFS (customized)

**AWS Console → search EFS → Create file system → Customize**

![Screenshot 01](images/01.png)

![Screenshot 02](images/02.png)

![Screenshot 03](images/03.png)

#### Step 2: Configure mount targets and the security group

In **Mount targets**, all Availability Zones are selected → **Add mount target** → select the **default security group**.

Copy the security group ID, open it in a new tab and edit the inbound rules: **Add rule → NFS, Anywhere → Save rules**.

![Screenshot 04](images/04.png)

![Screenshot 05](images/05.png)

![Screenshot 06](images/06.png)

![Screenshot 07](images/07.png)

![Screenshot 08](images/08.png)

Refresh both the **Security Group** tab and the **EFS** tab.

![Screenshot 09](images/09.png)

![Screenshot 10](images/10.png)

#### Step 3: Launch 3 instances with different operating systems

![Screenshot 11](images/11.png)

![Screenshot 12](images/12.png)

#### Step 4: Ubuntu instance: mount the EFS

Launch and connect to the Ubuntu instance.

![Screenshot 13](images/13.png)

Install the NFS client:

```bash
sudo apt update
sudo apt install nfs-common -y
```

![Screenshot 14](images/14.png)

![Screenshot 15](images/15.png)

Create a directory for the mount:

```bash
sudo mkdir efs
```

Go to **EFS → Attach**, copy the **NFS client** mount command and paste it into the terminal.

![Screenshot 16](images/16.png)

Verify the mount:

```bash
df -h
ls
pwd
cd efs
```

![Screenshot 17](images/17.png)

![Screenshot 18](images/18.png)

![Screenshot 19](images/19.png)

#### Step 5: Amazon Linux instance: mount the EFS and create a file

Launch and connect to the Amazon Linux instance. Install the NFS client, create a directory with the same name, mount the EFS with the **NFS client** command and move into the directory.

![Screenshot 20](images/20.png)

```bash
sudo yum update
sudo yum install nfs-utils
sudo mkdir efs
sudo mount -t nfs4 -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport fs-095c807f5f727bc36.efs.us-east-1.amazonaws.com:/ efs
df -h
cd efs
sudo nano amazon-linux.txt
```

File content:

```text
I am inside Amazon Linux machine
```

![Screenshot 21](images/21.png)

Save with **Ctrl + S** and exit with **Ctrl + X**.

```console
$ ls
amazon-linux.txt
```

![Screenshot 22](images/22.png)

#### Step 6: Ubuntu instance: create a file and read both files

```bash
sudo nano ubuntu.txt
```

File content:

```text
I am inside Ubuntu machine
```

![Screenshot 23](images/23.png)

![Screenshot 24](images/24.png)

```console
$ ls
amazon-linux.txt  ubuntu.txt
$ cat amazon-linux.txt
I am inside Amazon Linux machine
$ cat ubuntu.txt
I am inside Ubuntu machine
```

![Screenshot 25](images/25.png)

#### Step 7: Amazon Linux instance: read the Ubuntu file

```console
$ ls
amazon-linux.txt  ubuntu.txt
$ cat ubuntu.txt
I am inside Ubuntu machine
```

![Screenshot 26](images/26.png)

#### Step 8: Red Hat instance

Similarly, create and launch the **Red Hat** instance.

![Screenshot 27](images/27.png)

![Screenshot 28](images/28.png)

Select the default security group, click **Launch instance** and connect with an **SSH client**.

![Screenshot 29](images/29.png)

Go to **Downloads**, find the `redhat-key` file and copy its location. Paste it in **Windows PowerShell**, then paste the SSH client command as shown.

![Screenshot 30](images/30.png)

```bash
sudo yum update
sudo yum install nfs-utils
sudo mkdir efs
sudo mount -t nfs4 -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport fs-095c807f5f727bc36.efs.us-east-1.amazonaws.com:/ efs
```

![Screenshot 31](images/31.png)

```bash
sudo yum install nano
df -h
cd efs
sudo nano redhat.txt
```

File content:

```text
I am inside Redhat machine
```

![Screenshot 32](images/32.png)

> **Result:** All three files, created on three different operating systems, are visible from the Red Hat instance through the shared EFS (NFS).

---

## Case Study 1: Web Servers with AMI and EBS

**Problem statement:** You work for XYZ Corporation. Your corporation is working on an application and they require secured web servers on Linux to launch the application.

### Tasks

1. Create an instance in the US-East-1 (N. Virginia) region with Linux OS and manage the requirement of web servers of your company using AMI.
2. Replicate the instance in the US-West-2 (Oregon) region.
3. Build two EBS volumes and attach them to the instance in the US-East-1 (N. Virginia) region.
4. Delete one volume after detaching it and extend the size of the other volume.
5. Take a backup of this EBS volume.

### Solution

#### Task 1: Create a Linux instance in N. Virginia

![Screenshot 33](images/33.png)

![Screenshot 34](images/34.png)

#### Task 2: Replicate the instance in Oregon

**a. Create an AMI in N. Virginia**

![Screenshot 35](images/35.png)

**b. Copy the AMI to Oregon**

![Screenshot 36](images/36.png)

**c. Launch the replica in Oregon**

![Screenshot 37](images/37.png)

![Screenshot 38](images/38.png)

Click **Launch instance from AMI**.

![Screenshot 39](images/39.png)

#### Task 3: Create and attach two EBS volumes

Created 2 EBS volumes: **ebs1** and **ebs2**.

![Screenshot 40](images/40.png)

Attach each volume: select the volume → **Actions → Attach volume**.

![Screenshot 41](images/41.png)

![Screenshot 42](images/42.png)

![Screenshot 43](images/43.png)

Similarly, attach **ebs2**.

![Screenshot 44](images/44.png)

#### Task 4: Detach and delete one volume, extend the other

![Screenshot 45](images/45.png)

![Screenshot 46](images/46.png)

![Screenshot 47](images/47.png)

![Screenshot 48](images/48.png)

Increased the size of the volume from **10 GiB → 20 GiB**.

![Screenshot 49](images/49.png)

#### Task 5: Back up the EBS volume

Created a **snapshot of ebs1**.

![Screenshot 50](images/50.png)

![Screenshot 51](images/51.png)
