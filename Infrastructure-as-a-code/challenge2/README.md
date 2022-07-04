![#f03c15] # Practice-DevOps `#f03c15`
This repo contains my code solutions for infrastructure as a code part of the nanodegree 

In this challenge I'm builing this infra-diagram

<img src="awswebapp-2.jpeg">

![#1589F0] <h4 color="red">Template file ![#c5f015] network.yml `#c5f015`</h4> `#1589F0`
-Contains deployment for a VPC, with a pair of public and private subnets spread across two Availabilty Zones. It deploys an Internet Gateway, with a default 
route on the public subnets. It deploys a pair of NAT Gateways (one in each AZ), and default routes for them in the private subnets.

![#1589F0] <h4 color="red"> Parameters File ![#c5f015] network.yml `#c5f015`</h4> `#1589F0`
- It contains the list of parameters that are being used in the current CloudFormation template

 ![#c5f015] <h4>crete.sh</h4> `#c5f015`
This file contains the create-stack command, which expects three command-line arguments

 ![#c5f015] <h4>update.sh</h4> `#c5f015`

This file contains the update-stack command, and this too expects three command-line arguments.