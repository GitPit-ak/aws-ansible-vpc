# Complete ansible automation setup

### Flow of execution 

Launch a control machine provision ansible playbook (Manual)
requirement:
- ansible
- awscli
- iam user role with admin access attached into ec2

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

Ec2 (ansible)
- bastion host in public subnet
- 2 web server on each subnet

provision (ansible)
- write playbook to setup web server
