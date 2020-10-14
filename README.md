# SRE-Code-Test
 
## Overview
Hello and welcome to the Penn Interactive SRE applicant challenge.
 
Our hope is you find this challenging and exciting.  Each of the sections tackles one key aspect of the job responsibilities expected of a Site Reliability Engineer at Penn Interactive.  Some of these sections can be done without other sections, however most of the sections will build off of the last.
 
## Expectations
We do not expect every section of this challenge to be completed in the timeframe of the challenge.  Select the sections you feel are your strongest and focus on them.  The goal of the challenge is to see the breadth and depth of knowledge you, the candidate, have.  With that said here's some guidelines on our expectations:
1. A time limit is given for this challenge.  Any submissions after that time limit are not accepted.
1. This challenge must be taken by yourself.  This is a challenge of your knowledge and skill sets.
1. This repo must be cloned (not forked).  Your submission must be in your own cloned repo, the last commit before the time limit will be evaluated.  We honestly do not care how many commits there are to the repo / pull requests / etc.  You do not get bonus points for only one commit, in fact, we'll probably think you're a bit foolish.
1. If you are unsure how to technically do something, instead of submitting nothing, try submitting a text document outlining what steps you'd do to accomplish a task or to talk through it.  Part of being an SRE is thinking outside the box.
 
## Problem
 
### Section 1 - Infrastructure
 
For this section, all of your code must be in the infra folder.  At Penn Interactive, we're exclusively an AWS shop.  Also, we exclusively use terraform.
 
Scenario:
You've been asked by an engineering team to set up some type of container that accepts input from "www.somedomain.com".  They are going to hand you a Python 3.8 file which will be modified to run on the infrastructure that is prepared.  To begin with, the Python Code will only service two paths which are a GET and a POST at "/user".  However, more paths will be used in the future.  The code that they've written will need to speak with DynamoDB, also to be spun up in this ask.  Assume that the data being passed is highly sensitive and needs to be encrypted at all levels, in transit and at rest.  Any AWS services that offer additional protections should be provisioned as well.  As an SRE, we are highly concerned with availability, durability, and reliability of any application.  Please consider all aspects of that when provisioning this infrastructure.  Also, bear in mind that our logging analytics tool can acquire logs via an installed collector or via cloudwatch logs.
 
### Section 2 - Docker
 
For this section, all of your code must be in the docker folder.
 
Scenario:
You've been asked by an engineering team to help them set up a local testing environment for their python code.  Some engineers use Linux (and every distro under the sun), some use Macs but we want all of them to have the same experience when testing locally.  What they'd like is to have the dockerfile pull in their python file then execute it when run.  This python file takes input over port 5000 for dev purposes and for uniformity should be called on port 5000 locally.  This application produces logs in the "/var/log/app" directory, these should end up locally for analysis.
 
### Section 3 - Audit Script
 
For this section, all of your code must be in the auditscript folder.  This section must be written in either Bash, Python, or Go. 
 
We need to periodically audit our EC2 instances and generate a report.  This report is a table that has the following per row - InstanceID, Instance start time, size, total harddrive size.  This script needs to take an input of the region.  the output of this script should be a file, not a console output.  Ideally, this should be a CSV file for ease of viewing, but a text file is also acceptable.
 
### Section 4 - CI/CD
 
For this section, all of your code must be in the cicd folder.  Penn Interactive uses Jenkins, so ideally this section would yield a file or files that Jenkins can run.  Ideally, the majority of this should be written in Groovy.  Any section that cannot be written in Groovy should be in bash, python, or go.  Assume everything is running in AWS with proper IAM credentials.
 
You've been asked by an engineering team to help them automate a specific process.  This process is to run every 30 minutes.  This process consists of the following steps -
1. Grabs the hostname of the worker node and IP address and display to the screen.
1. Queries the Route53 records for "barstoolsportsbook.com", there will be exactly 2 weighted records.
1. Determine which record is "active" by seeing which record has 100 for the weight.  The other record will have 0 and is described as the "inactive" record.  If this is not the case, the job should fail.
1. Display which record is active and which is inactive.
 
### Section 5 - Static Infrastructure
 
For this section, all of your code must be in the staticinfra folder.  This section must be written using Ansible, Puppet, or Chef.  The script file should be written in either bash, python, or go.
 
You have been approached by an engineering team to help them have a repeatable set up of an EC2 instance.  They have given you free reign to use whatever flavor of Linux you'd like.  This file should do the following:
1. Creates and mounts an ebs volume at /example
1. Formats this volume using ext4
1. Has the volume persist when the machine is rebooted at /example
1. Updates the OS
1. Installs Python 3.8 and Pip3
1. Installs boto3 via Pip3
1. Creates or uploads a file to the server that gets the server's IP and hostname.  This file then writes that to /example/ip.txt and /example/hostname.txt respectively. (Create this file and have it in the folder as well)
1. Creates a cron job that runs the above file every 15 minutes
 
### Section 6 - Monitoring
 
For this section, you'll need to write out a detailed explanation inside the monitoring folder.
 
An engineering team has come to you to help them set up monitoring and alerting on their new middleware microservice.  This microservice logs all transactions with any information you would like.  This middleware connects to a Database (postgres), dynamoDB, and various third party APIs.  All of the logs are ingested into a logging tool.  What would you monitor on this middleware stack?  What thresholds would you alert on?
 
### Section 7 - Architecture
 
For this section, you'll need to write a detailed explanation as well as provide a diagram inside the architecture folder.
 
The Director of Architecture has approached you to design a highly scalable, and highly available three tiered application.  You must take all things of AWS into account and can use any and all AWS resources to accomplish this.  Do not worry about the code going in to this, it will be tailored to fit the design provided.  HINT: Be thorough.

