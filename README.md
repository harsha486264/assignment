# assignment
Nginx using Docker in AWS

# Setup your environment 

## AWS Account

* Create an AWS account

* Create IAM user and assign administration access "AdministratorAccess" policy.

* Download accesskey and secretkey of above user.

## AWS Local Environment

* Install AWS CLI (For this demo I am using Ubuntu as my local workstation)

* sudo apt-get update

* sudo apt-get install python-pip

* sudo pip install awscli

* aws configure (paste your accesskey and secretkey key which you downloaded)

    * accesskey

    * secretkey

    * region

    * output format

## Create ssh key

* ssh-keygen

## Import ssh key into AWS

* aws ec2 import-key-pair --key-name lncdemo --public-key-material file://~/.ssh/id_rsa.pub

## Setup ansible in your local environment

$ sudo apt-get update
$ sudo apt-get install software-properties-common
$ sudo apt-add-repository --yes --update ppa:ansible/ansible
$ sudo apt-get install ansible

## Create ansible roles

* vpc

* igw

* route tables

* subnets

* security groups

* mkdir lncdemo

* cd lncdemo

* mkdir roles

* cd roles

* mkdir -p vpc/{tasks,vars} igw/{tasks,vars} routetables/{tasks,vars} subnets sg/{tasks,vars}

## Create Security Group (open 22 and 80)

* aws ec2 create-security-group --group-name lncsg --description "LNC demo SG"

## Launch AWS instance (I am using us-east-1 and ubuntu AMI for this demo)

* aws ec2 run-instances --image-id ami-01ac7d9c1179d7b74 ---instance-type t2.micro --key-name lncdemo 
