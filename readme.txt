I found this a little tricky.   Fill in the variables as below:

AWS_ACCOUNT_ID = Your 12 digit AWS account ID
AWS_REGION = whatever region your ECR cluster is in
IMAGE_TAG = usually 'latest' 
IMAGE_REPO_NAME = Name of your ECR Repository
IMAGE_NAME = Name of your image


Make sure your IAM permissions are set for ECR and ECS for your service role.

Make sure to run your codebuild as 'priviledged'
I am using UBUNTU Standard Image, NOT AmazonLinux2 version3.

If using AmazonLinux2 docker image, make sure you add the aws-cli to the container,
usually with RUN sudo yum install awscli, because it seems that while Ubunut image 
comes with it pre-installed, AmazonLinux2 does not.

Also, remember to add 'run-as:' (usually codebuild-user) to the buildspec.yml
