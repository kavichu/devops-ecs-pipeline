# ECS python pipeline
This repository has the goal of showing how to create a stack to run a CD/CD pipeline running a python app on ECS

# Setting up dependencies
## Create bucket
```sh
aws s3api create-bucket \
    --region us-east-1 \
    --bucket ecs-python-continuous-deployment
```

## Cloud Formation templates for nested stack
```sh
aws s3 cp --recursive \
       ./templates \
       s3://ecs-python-continuous-deployment/templates
```

# Create Stack
```sh
aws --region us-east-1 \
    cloudformation create-stack \
    --capabilities CAPABILITY_IAM \
    --stack-name ecs-python-app \
    --template-body file://ecs-pipeline.yaml
```

# Clean up
```sh
aws --region us-east-1 \
    cloudformation delete-stack \
    --stack-name ecs-python-app
```
