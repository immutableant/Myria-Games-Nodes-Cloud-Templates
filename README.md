# Gala-Nodes-Cloud-Templates
A repository to store cloud templates to generate Gala Games Nodes architectures.

## Introduction
I am a node owner and operator and I have created this repository to help other node owners and operators. As a certified AWS Solutions Architect, I have designed this repository with the goal of finding the most cost-effective architectural solution to run nodes on AWS.

The templates provided here are intended to be used as-is solutions or as references, and I am also available for consulting to help provide a more custom solution for your needs.

## What does these template do
These template creates the following resources in AWS:

- Virtual Private Cloud (VPC)
- Internet Gateway
- VPC Gateway Attachment
- Subnets
- Security Group
- Route Table
- Route
- Route Table Association
- EC2 Launch Template
- Auto Scaling Groups

## Current Templates
- [AWS-2AZ-2Node-CF.yaml](https://github.com/immutableant/Gala-Nodes-Cloud-Templates/blob/main/templates/AWS/AWS-2AZ-2Node-CF.yaml)
This CloudFormation template is used to create a new Amazon VPC with two subnets in different Availability Zones. It also creates a security group that allows incoming SSH and custom port 4001 TCP traffic, and a Launch Template for the EC2 instance with various properties such as the Amazon Linux AMI to be used, the instance type(t3.medium), the block device mapping(60 GB), and the network interfaces. Additionally, the UserData section of the Launch Template includes commands to update the system, install Docker, and download and install the [Gala Node V3 Software](https://support.gala.games/posts/4612481-install-the-gala-node-software-on-ubuntu-linux). This also generate an Auto Scaling Group that will put a node on each of the availability zones for a total of two nodes.
- [AWS-1R-2AZ-Sch-2Node-CF.yaml](https://github.com/immutableant/Gala-Nodes-Cloud-Templates/blob/main/templates/AWS/AWS-1R-2AZ-Sch-2Node-CF.yaml) **WORK IN PROGRESS**. Does the same as the template above but runs only for a set ammount of hours.

## Instructions for usage
This template requires AWS CLI and AWS CloudFormation to run. You will need to have the following prerequisites:

- An Amazon Web Services account
- AWS Identity and Access Management (IAM) permissions
- If using CLI, have the [AWS Command Line Interface](https://aws.amazon.com/cli/) installed in your OS.

### Usage via AWS CLI
Clone the repository or download the AWS CloudFormation template file to your local machine.
Open a terminal or command prompt window and navigate to the location of the file.

Run the following command:

```shell
aws cloudformation create-stack --stack-name <stack-name> --template-body file://<file-name>.yaml --parameters ParameterKey=APIKey,ParameterValue=<api-key> ParameterKey=Workloads,ParameterValue=<workloads>
```

Replace `<stack-name>` with the name you want to give the stack, `<file-name>` with the path/name of the CloudFormation template file, `<api-key>` with your [**node API key**](https://support.gala.games/posts/4864059), and `<workloads>` with the workloads you want to run on the node.

### Usage via AWS Console
Clone the repository or download the AWS CloudFormation template file to your local machine. 
- Sign in to your [AWS Management Console](https://aws.amazon.com/)
- Open the AWS CloudFormation console.
- Click the Create Stack button.
- Select Upload a template file and click the Choose File button to select the CloudFormation template file.
- Enter a stack name and the necessary parameters;  `api-key` with your [**node API key**](https://support.gala.games/posts/4864059), and `workloads` with the workloads you want to run on the node.
- Click the Create button.

For more information on how to use AWS CloudFormation, please refer to the [AWS CloudFormation User Guide.](https://aws.amazon.com/documentation/cloudformation/)