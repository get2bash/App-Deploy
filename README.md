# App-deployment
## About
- Deploying a python app that displays the hostname and IP of ther underlaying server using AWS CloudFormation and ansible for infrastructure provisioning and server configuration respectively.

## Prerequisite
- Working ansible installation
- AWS credentials (access & secret key, ec2 ssh key)

## Network setup
- Create network stack ```aws cloudformation create-stack --stack-name AppDeploy --template-body file://network.yml  --parameters file://network-parameter.json --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM" --region=us-east-1```

## Server provisioning
- - Create network stack ```aws cloudformation update-stack --stack-name AppDeploy --template-body file://server.yml  --parameters file://server-parameter.json --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM" --region=us-east-1```

## Security
- AWS Access Key
Wrap your AWS credentials in an Ansible Vault file that are expected to contain two variables : aws_access_key and aws_secret_key
The playbooks expect the the Vault file to be named aws_keys.yml
````bash
ansible-vault create aws_keys.yml
[type in a password]
[type in aws_access_key: ...]
[type in aws_secret_key: ...]
````

## Tools
- [Ansible: Configuration management tool](https://www.ansible.com/)
- [AWS Cloudormation: A service that helps you model and set up your AWS resources](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html)
