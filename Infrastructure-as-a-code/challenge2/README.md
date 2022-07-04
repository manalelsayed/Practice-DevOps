 <h2># Practice-DevOps </h2>
This repo contains my code solutions for infrastructure as a code part of the nanodegree 

In this challenge I'm builing this infra-diagram

<img src="awswebapp-2.jpeg">

 <h4>Template file: network.yml</h4>
-Contains deployment for a VPC, with a pair of public and private subnets spread across two Availabilty Zones. It deploys an Internet Gateway, with a default 
route on the public subnets. It deploys a pair of NAT Gateways (one in each AZ), and default routes for them in the private subnets.

 <h4> Parameters File: parametrs.json</h4> 
- It contains the list of parameters that are being used in the current CloudFormation template

 <h4>create.sh</h4> 
This file contains the create-stack command, which expects three command-line arguments



 <h4>update.sh</h4>

This file contains the update-stack command, and this too expects three command-line arguments.

#Notes
-you must be in the origin speciefied in your create.sh file to see the cloudformation stacks

-To execute the Shell scripts write these commands in your bash cmd

./create.sh {here write your stack name} {template file name} {parameters file name}
ex: ./create.sh stackOne network.yml parameters.json

<h5>or you can directly write them in create.sh file but we don't want to hard-code these values to make our code reusable</h5>

The command above is equivalent of running the following:
aws cloudformation create-stack --stack-name stackOne --template-body file://network.yml    --parameters file://parameters.json  --region=us-west-2

-Troubleshoot
While running the AWS commands using either create.sh or update.sh file, if you face permission denied error,
then you will have to grant the execute permission to the owner (yourself) explicitly as:
chmod +x update.sh 
chmod +x create.sh 