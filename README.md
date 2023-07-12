# Complete ansible automation setup
![Cloud Architecture](https://github.com/GitPit-ak/aws-ansible-vpc/assets/44562876/d5d34464-8382-4d17-933e-64cdc3546ebd)


### Prerequisite

Launch a control machine provision ansible playbook (Manual)
requirement:
- ansible
- awscli
- iam user role with admin access attached into ec2
- clone this repo

### What will we have in this setup.
We have set up two private running web servers in separate availability zones (AZs) within our own Virtual Private Cloud (VPC). These servers are located in private subnets and are not directly accessible from the internet. Instead, we have a bastion/frontend server that acts as a gateway and is exposed to the internet.

To enable load balancing and distribute traffic evenly between the two web servers, we have configured an Elastic Load Balancer (ELB) using the round-robin method. The ELB sits in the public subnet and forwards incoming requests to the web servers in the private subnets.

Overall, our setup ensures that our web servers are kept safe within the private subnets while still allowing controlled access via the bastion/frontend server and load balancing through the ELB.


### Flow of execution 

- Install ansible
- goto repo folder and run the main.yml
    
    #######This playbook will setup
    - Complete Own VPC with NAT GW
    - Security groups for public and private ec2 instances
    - key-pair for our ec2 instances
    - launch 1 public(bastion) instance & 2 private Instance(web server's)
    - Create varible file which will execute on next step and copied into bastion home directory.

- Login into bastion server 
- You will get the repo folder on your home directory
- move to provision-ec2 folder and run the main.yml after instaling ansible on this server.
    #######This playbook will setup
    - Install requied pakages for web server
    - download dependency from the internet
    - setup and start the web server

 

### Flow of Plan 

Devops-VPC (ansible)

- vpc
- subnetting
    - 2 pubsub
    - 2 privpub
- IGW
- route Tables
 - attached igw into 2 pubsub
- NAT GW in public subnet
    - attached 2 priv subnet into NATGW

Security Groups (ansible)
- ELB-SG and Bastion Host-SG
- private server security groups

Create key pairs for ec2 intances
- bastion host
- 2 private servers

Ec2 (ansible)
- bastion host in public subnet
- 2 web server on each subnet

provision (ansible)
- write playbook to setup web server
