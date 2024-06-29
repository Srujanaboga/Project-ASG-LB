# Project-ASG-LB
AutoScalling Group with Load balancer hosting webservers

Tip

For instance level | maitain SG - http, https

SG | LB - http, https

Maintain path, port details and package on a instance level examples: maintain pkg add path /index.html
define port number 80
Path in case of Winodows - C:/intetpub/wwwroot/index.html
Path in case of Linux - var/www/html/index.html

Create Auto Scaling Group

Create Template | AMI - linux | Advanced >> Paste Script
Example

#!/bin/bash
yum update -y
yum install httpd -y
systemctl start httpd
systemctl enable httpd
usermod -a -G apache ec2-user
chmod 777 /var/www/html
cd /var/www/html
echo "<h1>hello from $(hostname -f) webserver</h1>">/var/www/html/index.html

Spot | On Demand
Desired Capacity | Maximum Capacity | Minimum Capacity
Attach Load Balancer to ASG
EC2 Console >>
Copy public ip - webserver | Browser
Crosscheck LB | Target Group* | Healthy
Load Balancer in Web Browser
Delete ASG | (Instances will be delete automatically)
Delete Target Group
Delete Load Balancer
