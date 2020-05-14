# Creating the stack for your EKS deployment

Deployment on EKS involves quite a few steps to setup.
This page provides a link in the bottom to a document that can help in creating the necessary resources on AWS. However, do make sure to read the following once before diving right in as it may contain answers to many queries you may have during the setup:
* At all times, the region code for the Mumbai services will be ap-south-1. Make sure to choose this to reduce latency in the services.
* The Step 0 in the article requests to have installed AWS IAM Authenticator. Do note that this will not be "necessary".
* In Step 1, there has been some changes since the article. Choose "EKS Cluster" as the use case while creating the role. The AmazonEKSServicePolicy is no longer required.
* In Step 2 and Step 4, you shall not be able to provide the same URL for uploading the template. Instead manually download the template on your system and upload the template where required.
* In the VPC creation step (Step 2), do provide any valid IP ranges from RFC 1918. Make sure your range does not collide with any other existing VPC.
* In the Node Group creation step (Step 4), execute `aws ssm get-parameter --name /aws/service/eks/optimized-ami/1.16/amazon-linux-2/recommended/image_id --query "Parameter.Value" --output text` on your command line replacing 1.16 with your cluster's kubernetes platform version. Use the value of the output as the Node Image ID.
* Follow the steps until and including Step 4 only.

Click [here](https://logz.io/blog/amazon-eks-cluster/) to setup the necessary AWS resources for your EKS deployment.