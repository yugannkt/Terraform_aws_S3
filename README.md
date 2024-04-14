# Terraform_aws_S3

## Terraform Workflow

The Terraform workflow consists of the following steps:
### Initialize: The terraform init command initializes the Terraform working directory and downloads the required providers.
### Plan: The terraform plan command generates an execution plan that describes the changes to be made to the infrastructure.
### Apply: The terraform apply command applies the changes to the infrastructure.
### Destroy: The terraform destroy command destroys the resources that were created by Terraform.
Here is an example of a Terraform workflow that creates an S3 bucket:

## Initialize:
` terraform init ` 

## Plan:
`terraform plan`

## Apply:
`terraform apply`

## Destroy:
` terraform destroy`

In this project, you used Terraform to create a public S3 bucket on AWS and upload a simple static website to it. The website consists of an index page (index.html), an error page (error.html), and a profile picture (profile.png).

Congire your aws access key and secret key

Here's a breakdown of the Terraform configuration files used in this project:

## Provider Configuration
The provider configuration specifies the AWS provider and the region where the resources will be created. In this project, you used the AWS provider and set the region to us-east-1.

## Resource Configuration
The resource configuration defines the resources to be created, such as S3 buckets, EC2 instances, and security groups. In this project, you created an S3 bucket, set the bucket ownership controls, public access block, and ACL, and uploaded the website files.
Here's a breakdown of the resource configuration:

S3 Bucket: The aws_s3_bucket resource creates an S3 bucket with the specified name. In this project, you set the bucket name to mynewtesttrailbucket.

Bucket Ownership Controls: The aws_s3_bucket_ownership_controls resource sets the bucket ownership controls to BucketOwnerPreferred, which means that the bucket owner has full control over the objects in the bucket.

Public Access Block: The aws_s3_bucket_public_access_block resource blocks public access to the bucket, except for the objects that have been explicitly made public.

Bucket ACL: The aws_s3_bucket_acl resource sets the ACL (Access Control List) of the bucket to public-read, which means that the objects in the bucket can be read by anyone.

S3 Objects: The aws_s3_object resources upload the website files to the S3 bucket.

S3 Bucket Website Configuration: The aws_s3_bucket_website_configuration resource configures the S3 bucket as a static website. It sets the index document to index.html and the error document to error.html.

### Variables
The variables.tf file defines the variable bucketname with a default value of mynewtesttrailbucket.

To apply the updated Terraform configuration and configure the S3 bucket as a static website, follow these steps:
1. Open a terminal or command prompt and navigate to the directory where you saved the Terraform configuration files.
2. Run the terraform plan command to generate an execution plan that shows what changes Terraform will make to the infrastructure.
3. Review the execution plan to ensure that it matches your expectations. If everything looks good, proceed to the next step.
4. Run the terraform apply command to apply the changes to the infrastructure. Terraform will prompt you to confirm that you want to proceed. Type yes to continue.
5. Wait for Terraform to finish configuring the S3 bucket as a static website. This may take a few minutes.
6. Once the Terraform apply completes, you can verify that the S3 bucket has been configured as a static website by using the AWS Management Console or the AWS CLI.

Here's an example of how to use the AWS CLI to verify that the S3 bucket has been configured as a static website:

`aws s3api get-bucket-website --bucket <your-bucket-name>`

Replace <your-bucket-name> with the name of your S3 bucket. This command should display the website configuration for the S3 bucket.
That's it! You have successfully configured the S3 bucket as a static website using Terraform. You can now access the website by using the URL http://<your-bucket-name>.s3-website-<region>.amazonaws.com, where <your-bucket-name> is the name of your S3 bucket and <region> is the AWS region where the bucket is located. For example, if your bucket name is mynewtesttrailbucket and it is located in the us-east-1 region, the URL of your website would be http://mynewtesttrailbucket.s3-website-us-east-1.amazonaws.com.
