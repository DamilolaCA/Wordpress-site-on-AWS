# Wordpress-site-on-AWS
This is a capstone project for wordpress site on AWS using VPC
## VPC Setup
- The Ip address range for the VPC was 10.0.0.0/16. This means the starting IP is 10.0.0.0 and the ending IP is 10.0.255.255 with total address 0f 65,536
![IPrange](./img/1.create-vpc-1.png)
- The VPC was suceessful created.
![VPC_creation](./img/2.vpc-sucessfully-created.png)
- The wordpress VPC subnets was created.
![creating_subnet](./img/3.creating-subnets-with-capstone-vpc.png)
- The wordpress VPC subnets was sucessfully created.
![subnet_created](./img/4.subnet-created.png)
- Private subnet was configure and cidr was set to 10.0.7.0/24 with 251 addresses
![private_subnet_created](./img/5.private-subnet-created.png)
- Public subnet was configure and cidr was set to 10.0.6.0/24 with 251 addresses.
- The cidr was choosing to avoid overlap between the public and private subnet.
- Different network zone was selected for the public and private to ensure availability.
![public_subnet_created](./img/6.public-subnet-created.png)
- Route tables was configured for each subnet.
![route_tables_created](./img/7.route-table-created.png)
- Subnets were associated with each subnet.
![route_subnet_ass](./img/9.associate-route-table-with-subnet.png)
## Public and Private Subnet with NAT Gateway.
- Creating internet gateway for public subnet.
![igw_created](./img/10.internet-gateway-creation.png)
- Attaching internet gateway to the wordpress VPC.
![igw_vpc](./img/11.igw-attached-to-vpc.png)
- Adding internet gate way to route table associated with public subnet internet access.
![igw_route_table_public_subnet](./img/12.adding-igw-route-table.png)
- Creating and configuring NAT gateway for private subnet interet access 
![NAT_gateway_created](./img/13.creating-Nat-gateway.png)
- Associating NAT gateway to private subnet for secure configuration.
![NAT_private_subnet](./img/14.private-subnet-ass-add-to-nat-gw.png)
- Visualizing VPC resource map to show that proper achitectures.
![VPC_resource_map](./img/15.vpc-resources-map.png)
## AWS MySQL RDS Setup
- RDS Instances was created
![rds_mysql_created](./img/18.rds-created-sucessfully.png)
- security group was configure for the rds with private subnet and NAT gateway for secure database internet access.
![RDS_SG](./img/19.sg-4-public-subnet.png)
- EC2 instances for wordpress web server was created. 
![EC2_wordpress_instances](./img/22.wordpress-ec2-launch.png)
- Security group was configured for the EC2 wordpress instances. 
![wordpress_sg_config](./img/24.SG-rule-for-EC2.png)
- Wordpress instances was connected to Amazon. 
![wordpress_connected](./img/25.ec2-connected.png)
- Mysql server was installed on linux. 
![install_mysql](./img/26.unstalling-mysql.png)
- RDS MySQL was configured for wordpress instances connection 
![Mysql_config](./img/27.configuring-mysql.png)
- Setting up user and login password for mysql and connecting the Wordpress to the mysql. 
![Mysql_connect_wordpress](./img/29.mysql-finally-configured.png)

## EFS Setup for WordPress Files
- Installing apache
![Install_apache](./img/30.install-apache-on-ec2-instances.png)
- starting apache
![starting_apache](./img/31.starting-apache-web-server.png)
- Testing install apache by loading the public IP on browser
![Test_apache](./img/32.testing-install-apache.png)
- Fetching wordpress files from the web and unzipping it.
![Install_apache](./img/33.getting%20EFS.png)
- Configuring EFS files for mounting on wordpress instance
![EFS_config](./img/35.wordpres-efs-cong.png)
- coping wordpress file to /var/www/html/ format
![wp_html](./img/36.wp-to-html.png)
- Testing the EFS setup and wordpress web
![wp_test](./img/37.wordpress-web-launch-test.png)

## Application Load Balancer and Auto Scaling
- creating target group for load balancing
![target_group](./img/39.create-target-group.png)
- creating load balancing and listener rules for routing traffic
![load_bal](./img/40.load-balancer-created.png)
- creating of auto scaling and integration with load balancer
![asg](./img/42.asg-created.png)
## Testing
The load balance was tested to ensure it function properly. Also, autoscalling was visualize to ensure the wordpress web deployment is cost effectives.