# IAAC-using-CloudFormation
Infrastructure as Code deployment with CloudFormation to deploy secure and highly available cloud infrastructure and web application in AWS
This projects consists of two scripts (in YAML) that create and deploy the IaaC ( Infrastructure as Code ) templates using CloudFormation.

The first script deploy the network infrastructure as it creates :
	- a VPC and attach an IGW to this VPC.
	- four subnets(two public and two private) in different AZs to make the servers highly available.
	- Nat Gatways in the public subnets to allow outbound internet access for Ec2 instances
 
The second script deploy the servers components in addition to security groups, and the required software for each server: 

	- An Auto scaling Group to provide elasticity, this ASG has the required Launch Configuration for Ec2 instances such as: 
		  - IAM role to allow the Ec2 instance to access the S3 Bucket that contains the webapp.
		  -user data to install all required dependencies for servers.

	-Two internet facing load balancers in public subnets acting as entry point to the cloud enviroment and then forward the traffic evenly to the target Ec2 intances located in the    private subnets.
