# Cloudformation-app-deployment

## Prerequisite
- Working ansible installation
- AWS credentials (access & secret key, ec2 ssh key)

## AWS Access Key
Wrap your AWS credentials in an Ansible Vault file that are expected to contain two variables : aws_access_key and aws_secret_key
The playbooks expect the the Vault file to be named aws_keys.yml
````bash
ansible-vault create aws_keys.yml
[type in a password]
[type in aws_access_key: ...]
[type in aws_secret_key: ...]
````
