# miniproject-WOLF-RICHARD

Hello! Thanks for checking out my mini-project. I've added three different CloudFormation to complete the task; EC2, Autoscale, and S3 static. All have different use cases, and wanted to demostrate TaskCat's ability to test multiple templates simultaneously.

To automate the process I'd use CodePipeline, but creating a CloudFormation template to implement a pipeline falls outside the scope of this project.

## EC2 Web Server

[![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=EC2WebServer&templateURL=https://s3-us-west-2.amazonaws.com/stelligent-wolf-richard/ec2webserver.template)

## Autoscale

[![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=S3Static&templateURL=https://s3-us-west-2.amazonaws.com/stelligent-wolf-richard/autoscale.template)

CloudFormation will give you a URL from the Output

## S3 Static

[![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=S3Static&templateURL=https://s3-us-west-2.amazonaws.com/stelligent-wolf-richard/s3static.template)

CloudFormation will give you two outputs you need; S3Bucket and WebsiteURL. While cfn created the infastructure the index file still needs to be copied to the S3 bucket using the aws cli.

aws s3 cp cfn-miniproject/html/index.html s3://S3Bucket/ --recursive

# Testing

## Installing TaskCat

### Installing TaskCat (Docker install)
> Prerequisites: docker
```
curl -s https://raw.githubusercontent.com/aws-quickstart/taskcat/master/installer/docker-install-master| sudo python -E
```
> Note: (If you do not have root privileges taskcat will install in the current directory)

### Installing via pip3 (for those who do not want to use the docker installer)
> Prerequisites: Python 3.5+ and pip3
```
pip3 install taskcat
```
### Running TaskCat
> A basic demonstartion 
```
taskcat -c cfn-miniproject/ci/demo.yml
```

This will create a taskcat_outputs file, open index.html in your browser for results

> For the full show, you need to edit ci/ec2-test.json and ci/autoscale-test.json

You will need KeyName, VpcId, Subnets, OperatorEMail for the test to run. Pretty enjoyable to watch.

```
taskcat -c cfn-miniproject/ci/taskcat.yml
```




