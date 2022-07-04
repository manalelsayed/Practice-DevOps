 <h2># challenge2 </h2>

In this challenge I'm builing this infra-diagram

<img src="awswebapp-2.jpeg">

 <h4>Template file: network.yml</h4>
-Contains deployment for the resources

 <h4> Parameters File: parametrs.json</h4> 
- It contains the list of parameters that are being used in the current CloudFormation template

 <h4>create.sh</h4> 
This file contains the create-stack command, which expects three command-line arguments



 <h4>update.sh</h4>

This file contains the update-stack command, and this too expects three command-line arguments.

<h3>Notes</h3>
-you must be in the origin speciefied in your create.sh file to see the cloudformation stacks <br>

-To execute the Shell scripts write these commands in your bash cmd<br>

./create.sh {here write your stack name} {template file name} {parameters file name}
<h4>ex: ./create.sh stackOne network.yml parameters.json</h4>

<h5>or you can directly write them in create.sh file but we don't want to hard-code these values to make our code reusable</h5>

The command above is equivalent of running the following:
<h4>aws cloudformation create-stack --stack-name stackOne --template-body file://network.yml  --parameters file://parameters.json  --region=us-west-2</h4>

<h3>Troubleshoot</h3>
While running the AWS commands using either create.sh or update.sh file, if you face permission denied error,
then you will have to grant the execute permission to the owner (yourself) explicitly as:<br>
chmod +x update.sh 
chmod +x create.sh 

<h2>Steps</h2>
<ol>
<li>Creates a VPC<br>
It will accept the IP Range -also known as CIDR block- from an input parameter</li>
<li>Creates and attaches an Internet Gateway to the VPC</li>
<li>Creates Two Subnets within the VPC with Name Tags to call them “Public” and “Private”<br>
These will also need input parameters for their ranges, just like the VPC.</li>
<li>The Subnet called “Public” needs to have a NAT Gateway deployed in it<br>
This will require you to allocate an Elastic IP that you can then use to assign it to the NAT Gateway.</li>
<li>The Public Subnet needs to have the MapPublicIpOnLaunch property set to true. Use this reference for help.</li>
<li>The Private Subnet needs to have the MapPublicIpOnLaunch property set to false.</li>
<li>Both subnets need to be /24 in size.<br>
If you need assistance with IP math, you can use a subnet calculator such as this one.</li>
<li>You will need 2 Routing Tables, one named Public and the other one Private</li>
<li>Assign the Public and Private Subnets to their corresponding Routing table</li>
<li>Create a Route in the Public Route Table to send default traffic ( 0.0.0.0/0 ) to the Internet Gateway you created</li>
<li>Create a Route in the Private Route Table to send default traffic ( 0.0.0.0/0 ) to the NAT Gateway</li>
<li>Finally, once you execute this CloudFormation script, you should be able to delete it and create it again, over and over in a predictable and repeatable manner, this is the true verification of working Infrastructure-as-Code</li>
</ol>