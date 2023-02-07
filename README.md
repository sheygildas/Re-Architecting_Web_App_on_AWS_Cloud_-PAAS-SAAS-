
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

<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>

### :lock: Create Security groups

<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>

### :bulb: Create Instances 

<br/>
<div align="right">
    <b><a href="#Project-04">↥ back to top</a></b>
</div>
<br/>

#### RDS


<br/>
<div align="right">
    <b><a href="#Project-04">↥ back to top</a></b>
</div>
<br/>

#### Amazon Elastic Cache

<br/>
<div align="right">
    <b><a href="#Project-04">↥ back to top</a></b>
</div>
<br/>

#### Amazon Active MQ

<br/>
<div align="right">
    <b><a href="#Project-04">↥ back to top</a></b>
</div>
<br/>

### Create Elastic Beanstalk Environment

<br/>
<div align="right">
    <b><a href="#Project-04">↥ back to top</a></b>
</div>
<br/>

### Update SG of Backend to Allow traffic from Bean SG

<br/>
<div align="right">
    <b><a href="#Project-04">↥ back to top</a></b>
</div>
<br/>

### Update SG of Backend to Allow Internal Traffic

<br/>
<div align="right">
    <b><a href="#Project-04">↥ back to top</a></b>
</div>
<br/>

### Launch Ec2-Instance for DB Initializing

<br/>
<div align="right">
    <b><a href="#Project-04">↥ back to top</a></b>
</div>
<br/>

### Login to the instance and Initialize RDS DB

<br/>
<div align="right">
    <b><a href="#Project-04">↥ back to top</a></b>
</div>
<br/>

### Change Health Check on Beanstalk at /login

<br/>
<div align="right">
    <b><a href="#Project-04">↥ back to top</a></b>
</div>
<br/>

### Add 443 HTTPS Listener to ELB

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

