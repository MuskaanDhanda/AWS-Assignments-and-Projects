# Project - 1: Deploying a Multi-Tier Website Using AWS EC2

## Description:
   Amazon Elastic Compute Cloud (Amazon EC2) provides scalable computing capacity in the Amazon Web Services (AWS) cloud. Using Amazon EC2 eliminates your need to invest in hardware up front so you can develop and deploy applications faster. You can use Amazon EC2 to launch as many or as few virtual servers as you need, configure security and networking, and manage storage. Amazon EC2 enables you to scale up or down to handle changes in requirements or spikes in popularity, reducing your need to forecast traffic.
## Problem Statement:
Company ABC wants to move their product to AWS. They have the following things set up right now:
1. MySQL DB
2. Website (PHP)
The company wants high availability on this product, therefore wants Auto Scaling to be enabled on this website.

# "Solution"
## Steps To Solve:

1. Create an RDS Instance
   <img width="1366" height="768" alt="image" src="images/01.png" />
   select Databases > create Database
   <img width="1366" height="768" alt="image" src="images/02.png" />
   <img width="1366" height="768" alt="image" src="images/03.png" />
   <img width="1366" height="768" alt="image" src="images/04.png" />
  Database name: intel Database & password: intel123
   <img width="1366" height="768" alt="image" src="images/05.png" />
   <img width="1366" height="768" alt="image" src="images/06.png" />
   <img width="1366" height="768" alt="image" src="images/07.png" />
   created RDS Database
   <img width="1366" height="768" alt="image" src="images/08.png" />
   
2. Launch an EC2 Instance
   <img width="1366" height="768" alt="image" src="images/09.png" />
   <img width="1366" height="768" alt="image" src="images/10.png" />
   <img width="1366" height="768" alt="image" src="images/11.png" />
   <img width="1366" height="768" alt="image" src="images/12.png" />

3. Allow all-traffic to EC2 instance
   Click instance ID :
   <img width="1366" height="768" alt="image" src="images/13.png" />
   <img width="1366" height="768" alt="image" src="images/14.png" />
   Click edit inbound rules > add rule
   <img width="1366" height="768" alt="image" src="images/15.png" />
   Save rules
   Connect the EC2 instance
   <img width="1366" height="768" alt="image" src="images/16.png" />
   <img width="1366" height="768" alt="image" src="images/17.png" />
   <img width="1366" height="768" alt="image" src="images/18.png" />

4. Allow traffic from EC2 to RDS instance
   <img width="1366" height="768" alt="image" src="images/19.png" />
   <img width="1366" height="768" alt="image" src="images/20.png" />
   All traffic already there therefore seems good

   
## Commands to be runned in EC2 
    1  sudo apt update
    2  sudo apt install apache2 -y
    3  sudo apt install php -y
    4  sudo apt install php-mysql -y
    5  sudo apt install libapache2-mod-php -y
    6   sudo apt install mysql-client -y
    7  sudo systemctl start apache2

   > paste public ip in browser using http
  <img width="1366" height="768" alt="image" src="images/21.png" />
  <img width="1366" height="768" alt="image" src="images/22.png" />

    11  cd /var/www/html
    12  ls
    13  sudo rm -r index.html
    14  sudo nano index.php

 ##   code file paste 
``` <html>
<link rel="stylesheet" href="https://bootstrapcdn.com">
<body background="images/2.png" style="background-repeat:no-repeat;
background-size: 100% 100%">
<br><br><br><br>
<div class="container">
  <div class="jumbotron vertical-center">
  	<table class="grid" cellspacing="0">
  		<tr>
  <td colspan="4">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td>
  <td colspan="4">
  	<form method="post">
  <div class="form-group" action="post">
    <label for="firstname">Name:</label>
    <input type="text" class="form-control" name="firstname">
  </div>
  <div class="form-group">
    <label for="email">Email:</label>
    <input type="text" class="form-control" name="email">
  </div>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<button type="submit" class="btn btn-success">Submit</button>
</form></td>  
  <td colspan="4"></td>
</tr>
</table>
</div>
</div>
<?php
$firstname=$_POST['firstname'];
$email=$_POST['email'];
$servername = "database-1.cgz0se208bpg.us-east-1.rds.amazonaws.com";
$username = "intel";
$password = "intel123";
$db = "intel";
// Create connection
$conn = new mysqli($servername, $username, $password, $db);

// Check connection
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}
if(isset($_POST['firstname']) && isset($_POST['email'])){
$sql = "INSERT INTO data (firstname,email)
VALUES ('".$firstname."', '".$email."')";

if ($conn->query($sql) === TRUE) {
    echo "New record created successfully";
} else {
    echo "Error: " . $sql . "<br>" . $conn->error;
}

$conn->close();
}
?>
</body>
</html>
```

      ls
   refresh the browser 
   <img width="1366" height="768" alt="image" src="images/23.png" />
          
      sudo systemctl restart apache2
       mysql -h database-1.cgz0se208bpg.us-east-1.rds.amazonaws.com -uintel -pintel123

  <img width="1366" height="768" alt="image" src="images/24.png" />
  
5. Create Database & Table in RDS instance:
a. Database name: intel
b. Table name: data
c. Database password: intel123
6. Change hostname in website

   <img width="1366" height="768" alt="image" src="images/25.png" />
   <img width="1366" height="768" alt="image" src="images/26.png" />


   go to browser and type
  <img width="1366" height="768" alt="image" src="images/27.png" />
   submit

   
# RESULT

   <img width="1366" height="768" alt="image" src="images/28.png" />
  





   
   











