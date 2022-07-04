 <h2 style="color:#f03c15;"># Practice-DevOps </h2>
This repo contains my code solutions for infrastructure as a code part of the nanodegree 

In this challenge I'm builing this infra-diagram

<img src="awswebapp-2.jpeg">

 <h4 style="color:#1589F0;">Template file <span style="color:#c5f015;">network.yml</span></h4>
-Contains deployment for a VPC, with a pair of public and private subnets spread across two Availabilty Zones. It deploys an Internet Gateway, with a default 
route on the public subnets. It deploys a pair of NAT Gateways (one in each AZ), and default routes for them in the private subnets.

 <h4 style="color:#1589F0;"> Parameters File  <span style="color:#c5f015;">parametrs.json</span> </h4> 
- It contains the list of parameters that are being used in the current CloudFormation template

 <h4 style="color:#c5f015;">crete.sh</h4> 
This file contains the create-stack command, which expects three command-line arguments

 <h4 style="color:#c5f015;">update.sh</h4>

This file contains the update-stack command, and this too expects three command-line arguments.