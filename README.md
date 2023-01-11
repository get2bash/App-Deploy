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

![Screen Shot 2023-01-11 at 7 24 50 PM](https://user-images.githubusercontent.com/97449891/211889362-d41b5e5e-044b-4045-b27c-838948fb1820.png)
![Screen Shot 2023-01-11 at 7 26 02 PM](https://user-images.githubusercontent.com/97449891/211889444-1b5ad1f5-0ae1-4ee8-956e-1ed755882a4c.png)


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

