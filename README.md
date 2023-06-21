# PART-1 = CI = CodeCommit + CodeBuild

# AWS CodeCommit repository needs to be created on AWS.
https://us-east-1.console.aws.amazon.com/codesuite/codecommit/repositories/CI-CD/browse?region=us-east-1
my AWS Code Commit repo name is CI-CD

# clone it 
git clone https://git-codecommit.us-east-1.amazonaws.com/v1/repos/CI-CD

# create and upload all the files for node.js, .html, .css files to AWS CodeCommit repo

# AWS CodeBuild with Ubuntu OS
https://us-east-1.console.aws.amazon.com/codesuite/codebuild/projects/CI/edit/artifacts?region=us-east-1

# build spec file to build a docker image
buildspec.yml

# after docker image is built, change the artifact from "no artifact" to S3 using "Edit Arftifact"

# create a S3 bucket 
https://s3.console.aws.amazon.com/s3/buckets/sam-artifact-demo-app?region=us-east-1&tab=objects

# re-Run CodeBuild to build the project 
https://us-east-1.console.aws.amazon.com/codesuite/codebuild/940319630789/projects/CI/build/CI%3Abc6003a0-a3e4-4cec-82f7-70f850dac482?region=us-east-1

# CI is built
https://s3.console.aws.amazon.com/s3/object/sam-artifact-demo-app?region=us-east-1&prefix=CI-CD.zip

====================================================================================================


# PART-2 = CodeDeploy
# launch a EC2 Ubuntu t2-micro machine
# create a service role for EC2 and give it full access on EC2, CodeDeploy & S3
# similarly, create a service role for CodeDeploy and give it full access on EC2, CodeDeploy & S3. Select use case as CodeDeploy

# run CodeDeployAgent.sh on EC2 which would deploy the app (sam-website) from S3 (.zip built project) to EC2 Ubuntu t2-micro instance

# create CodeDeploy application
# create Deployment group
# create deployment
https://us-east-1.console.aws.amazon.com/codesuite/codedeploy/application/CD/deployments/new?deploymentGroupName=CD-depl-grp&region=us-east-1

# check the files
/var/www/html
/var/www/html/scripts

# test if the application (sam-website) is running 
curl -L http://3.88.8.244

# test on browser
http://3.88.8.244








