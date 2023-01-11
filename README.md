# App-deployment
## About
- Deploying a python app that displays the hostname and IP of ther underlaying server using AWS CloudFormation for infrastructure provisioning and server configuration.

## Prerequisite
- AWS CLI
- AWS credentials (access & secret key, ec2 ssh key)

## Network setup
- Create network stack ```aws cloudformation create-stack --stack-name network --template-body file://network.yml --parameters file://network-parameter.json --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM" --region=us-east-1```

## Server provisioning
- Create network stack ```aws cloudformation create-stack --stack-name server --template-body file://server.yml --parameters file://server-parameter.json --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM" --region=us-east-1```

## The UseData will:
- Update the server
- Install all required tools
- Clone the app repo
- Configure nginx, ufw and systemd
- Enable and start services

## Running the App using Gunicorn
```gunicorn --workers=2 app:app —daemon```

## Logical network
![Flowcharts](https://user-images.githubusercontent.com/97449891/211727648-28ad767a-1364-43e4-9ae2-4b7784cb657f.jpeg)


## Tools
- [AWS CloudFormation: A service that helps you model and set up your AWS resources.](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html)
- [Gunicorn: Gunicorn 'Green Unicorn' is a Python WSGI HTTP Server for UNIX.](https://gunicorn.org/)

