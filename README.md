
# Project-04
## :ledger: Index

- [About The Project](#beginner-about-the-project)
- [Problem that this project solves ](#question-problem-that-this-project-solves)
- [Solution to the problem.](#key-solution-to-the-problem)
- [Tools](#hammer_and_wrench-Tools)
- [Architecture of this project](#house-architecture-of-this-project)
- [Steps to execute the project](#zap-steps-to-execute-the-project)
  - [Login to AWS Account ](#key-login-to-aws-account )
  - [Create Key Pairs](#closed_lock_with_key-create-key-pairs)
  - [Create Security groups](#lock-create-security-groups)
  - [Create Instances](#bulb-create-instances) 
  - [Create Elastic Beanstalk Environment](#bulb-create-elastic-beanstalk-environment)
  - [Update SG of Backend to Allow traffic from Bean SG](#bulb-update-sg-of-backend-to-allow-traffic-from-bean-sg)
  - [Update SG of Backend to Allow Internal Traffic](#bulb-update-sg-of-backend-to-allow-internal-traffic)
  - [Launch Ec2-Instance for DB Initializing](#bulb-launch-ec2-nstance-for-db-initializing)
  - [Login to the instance and Initialize RDS DB](#bulb-login-to-the-instance-and-initialize-rds-db)
  - [Change Health Check on Beanstalk at /login](#bulb-change-health-check-on-beanstalk-at-/login)
  - [Add 443 HTTPS Listener to ELB](#bulb-add-443-https-listener-to-elb)
  - [Build Artifact with Backend Information](#bulb-build-artifact-with-backend-information)
  - [Deploy Artifact to Beanstalk](#bulb-deploy-artifact-to-beanstalk)
  - [Create CDN with SSL Certificate](#bulb-create-cdn-with-ssl-certificate)
  - [Update Entry in DNS Zones](#bulb-update-entry-in-dns-zones)
- [Verify from browser](#earth_africa-verify-from-browser) 
- [Resources](#page_facing_up-resources)
- [Credit/Acknowledgment](#star2-creditacknowledgment)


## :beginner:About The Project

<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>

## :question: Problem that this project solves 

<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>

## :key: Solution to the problem.

<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>

## :hammer_and_wrench: Tools
- A tool
- B tool

| Name | Description |
| --- | --- |
| [`@toast-ui/editor-plugin-chart`](https://github.com/nhn/tui.editor/tree/master/plugins/chart) | Plugin to render chart |
| [`@toast-ui/editor-plugin-code-syntax-highlight`](https://github.com/nhn/tui.editor/tree/master/plugins/code-syntax-highlight) | Plugin to highlight code syntax |
| [`@toast-ui/editor-plugin-color-syntax`](https://github.com/nhn/tui.editor/tree/master/plugins/color-syntax) | Plugin to color editing text |
| [`@toast-ui/editor-plugin-table-merged-cell`](https://github.com/nhn/tui.editor/tree/master/plugins/table-merged-cell) | Plugin to merge table columns |
| [`@toast-ui/editor-plugin-uml`](https://github.com/nhn/tui.editor/tree/master/plugins/uml) | Plugin to render UML 

<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>

## :hammer_and_wrench: Prerequisites

- visual studio code
- AWS Account
- Maven
- Registered DNS Name
- JDK8

<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>

## :cloud: AWS Services
- EC2 instance
- ELB
- Autoscalling
- S3
- Ebs
- Route 53
- Elastic Beanstalk
- RDS
- Amazon MQ
- ElastiCache
- 
<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>


## :beginner: Architecture of this project.

![Project Image](project-image-url)

<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>

## :zap: Steps to Execute the project. 

<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>

### :key: Login to AWS Account


<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>

### :closed_lock_with_key: Create Key Pairs

- Create the  key pair that you use to login to your AWS services and name it as follows.

 ```sh
Name: vprofile-bean-key
   ```
   
![Project Image](project-image-url)  
   
<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>

### :lock: Create Security groups

- Create a security group for the `backend services` and name it `vprofile-backend-SG`. 
- Set `inbound rules` to allow  `11211`for Memcached, `5672` for RabbitMQ and port `3306` for MySQL server.
- Note: application.properties file found under [src/main/resources](https://github.com/sheygildas/Local_App_Setup/tree/local-setup/src/main/resources) directory, contain all the port rhat have to be open for our application services to communicate each other. 
- Allow all traffic from backends' own security group so that the backend services can communicate with each other.


![Project Image](project-image-url)
 
<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>

### :bulb: Create Instances 
- We will create all the instances for our project below.
<br/>
<div align="right">
    <b><a href="#Project-04">↥ back to top</a></b>
</div>
<br/>

#### Create RDS

- Before creating our RDS instance, let's first of all creat the `Subnet Groups` of our RDS with below details.

```sh
Name of subnet group: vprofile-rds-sub-grp
AZ: Select All
Subnet: Select All
   ```
- let's also create a `parameter group` for our RDS instance with the details below.

```sh
Parameter group family: mysql5.7
Type: DB Parameter Group
Group Name: vprofile-rds-para-grp
   ```

- Now let's create our RDS instances with the following details.


```sh
Method: Standard Create
Engine Options: MySQL
Engine version: 5.7.33
Templates: Free-Tier
DB Instance Identifier: vprofile-rds-mysql
Master username: admin
Password: Auto generate psw
Instance Type: db.t2.micro
Subnet grp: vprofile-rds-sub-grp
SecGrp:  vprofile-backend-SG
No public access
DB Authentication: Password authentication
Additional Configuration
Initial DB Name: accounts
Keep the rest default or you may add as your own preference
   ```
- When you clicking `Create button`, a popup window will come out proceed and click on `view credential` details then write down RDS pass that has been generated.

![Project Image](project-image-url)


<br/>
<div align="right">
    <b><a href="#Project-04">↥ back to top</a></b>
</div>
<br/>

#### Create Amazon Elastic Cache

- We will start by creating the `Subnet Groups` of the Elastic cache with the details below

```sh
Name: vprofile-memcached-sub-grp
AZ: Select All
Subnet: Select All
   ```

- let's also create a `parameter group` for our elastic cache instance with the details below.

```sh
Name: vprofile-memcached-para-grp
Description: vprofile-memcached-para-grp
Family: memcached1.4
   ```
- Finally we will create the Memcached Cluster with the details below. To create the cluster, go to `Get Started` -> `reate Clusters` -> `Memcached Clusters`

```sh
Name: vprofile-elasticache-svc
Engine version: 1.4.5
Parameter Grp: vprofile-memcached-para-grp
NodeType: cache.t2.micro
number of Nodes: 1
SecGrp: vprofile-backend-SG
   ```

![Project Image](project-image-url)


<br/>
<div align="right">
    <b><a href="#Project-04">↥ back to top</a></b>
</div>
<br/>

#### Create Amazon Active MQ

- Create Amazon MQ service with the details below. Remeber to write down the password of MQ.

```sh
Engine type: RabbitMQ
Single-instance-broker
Broker name: vprofile-rmq
Instance type: mq.t3.micro
username: rabbit
psw: bunnyhole789
Additional Settings:
private Access
VPC: use default
SEcGrp: vprofile-backend-SG
   ```

<br/>
<div align="right">
    <b><a href="#Project-04">↥ back to top</a></b>
</div>
<br/>

### Launch Ec2-Instance for DB Initializing

- Go to RDS instance and copy your DB endpoint.

```sh
vprofile-rds-mysql.b6hrgxmhxkpvxt.us-east-1.rds.amazonaws.com
   ```

- Create EC2 instance to initialize the DB. Terminated ths instance after the DB initialization.

```sh
Name: mysql-client
OS: ubuntu 18.04
t2.micro
SecGrp: Allow SSH on port 22
Keypair: vprofile-prod-key
Userdata:
#! /bin/bash
apt update -y
apt upgrade -y
apt install mysql-client -y
   ```
 
 <br/>
<div align="right">
    <b><a href="#Project-04">↥ back to top</a></b>
</div>
<br/

### Login to the instance and Initialize RDS DB

- SSH into mysl-client instance. We can check mysql version.


```sh
mysql -V
   ```
   
- RUN the following command with your db endpoint.


```sh
mysql -h vprofile-rds-mysql.chrgxmhxkprk.us-east-1.rds.amazonaws.com -u admin -p<db_password>
mysql> show databases;
   ```
- Clone the source code of this current github repository to use script to initialize our database. RUN the following commands and when you are done, you should be able to see 2 tables role, `user`, and `user_role`

```sh
git clone https://github.com/sheygildas/Re-Architecting_Web_App_on_AWS_Cloud_-PAAS-SAAS-.git
cd Re-Architecting_Web_App_on_AWS_Cloud_-PAAS-SAAS-
cd src/main/resources
mysql -h vprofile-rds-mysql.chrgxmhxkprk.us-east-1.rds.amazonaws.com -u admin -padvPtIYOfqGe4T41MUXk accounts < db_backup.sql
mysql -h vprofile-rds-mysql.chrgxmhxkprk.us-east-1.rds.amazonaws.com -u admin -padvPtIYOfqGe4T41MUXk accounts
show tables;
   ```
   

### Create Elastic Beanstalk Environment
-  Copy all the endpoints of our backend services through AWS console. These information will be used in our `application.properties file`

```sh
DS:
vprofile-rds-mysql.b6hrgxmhxkpvxt.us-east-1.rds.amazonaws.com:3306
ActiveMQ: amqps://c-a7d7aacb-4894-3af7-9048-726a9ceabc89.mq.us-east-1.amazonaws.com:5671
ElastiCache:
vprofile-elasticache-svc.cqmvsw.cfg.use1.cache.amazonaws.com:11211
   ```
- Now, let's set up Application in Elastic Beanstalk with the following details.

```sh
Name: vprofilejavaapp-prod-rd
Platform: Tomcat
keep the rest default
Configure more options:
- Custom configuration
****Instances****
EC2 SecGrp: vprofile-backend-SG
****Capacity****
LoadBalanced
Min:2
Max:4
InstanceType: t2.micro
****Rolling updates and deployments****
Deployment policy: Rolling
Percentage :50 %
****Security****
EC2 key pair: vprofile-bean-key
   ```
   
<br/>
<div align="right">
    <b><a href="#Project-04">↥ back to top</a></b>
</div>
<br/>
   
### Update SG of Backend to Allow traffic from Bean SG

- Update `vprofile-backend-SG` to allow connection from our application Security Group created by Beanstalk on port 3306, 11211 and 5671


```sh
Custom TCP 3306 from Beanstalk SecGrp
Custom TCP 11211 from Beanstalk SecGrp
Custom TCP 5671 from Beanstalk SecGrp
   ```
![Project Image](project-image-url) 


<br/>
<div align="right">
    <b><a href="#Project-04">↥ back to top</a></b>
</div>
<br/>


### Update SG of Backend to Allow Internal Traffic

```sh
Custom TCP 3306 from Beanstalk SecGrp
Custom TCP 11211 from Beanstalk SecGrp
Custom TCP 5671 from Beanstalk SecGrp
   ```

- Update `vprofile-backend-SG` to allow Internal Traffic
<br/>
<div align="right">
    <b><a href="#Project-04">↥ back to top</a></b>
</div>
<br/>


### Change Health Check on Beanstalk at /login

- In Elastic Beanstalk console, under our app environment, we need to clink Configuration and do below changes and apply


```sh
Processes: Health check path : /login
   ```
<br/>
<div align="right">
    <b><a href="#Project-04">↥ back to top</a></b>
</div>
<br/>

### Add 443 HTTPS Listener to ELB

- In Elastic Beanstalk console, under our app environment, we need to clink Configuration and do below changes and apply


```sh
Add Listener HTTPS port 443 with SSL cert
   ```
<br/>
<div align="right">
    <b><a href="#Project-04">↥ back to top</a></b>
</div>
<br/>

### Build Artifact with Backend Information

<br/>
<div align="right">
    <b><a href="#Project-04">↥ back to top</a></b>
</div>
<br/>

### Deploy Artifact to Beanstalk

### Create CDN with SSL Certificate

<br/>
<div align="right">
    <b><a href="#Project-04">↥ back to top</a></b>
</div>
<br/>
### Update Entry in DNS Zones


<br/>
<div align="right">
    <b><a href="#Project-04">↥ back to top</a></b>
</div>
<br/>
## :earth_africa: Verify from browser

<br/>
<div align="right">
    <b><a href="#Project-04">↥ back to top</a></b>
</div>
<br/>

## :page_facing_up: Resources

<br/>
<div align="right">
    <b><a href="#Project-04">↥ back to top</a></b>
</div>
<br/>


## :star2: Acknowledgment


<br/>
<div align="right">
    <b><a href="#Project-04">↥ back to top</a></b>
</div>
<br/>

