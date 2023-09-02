# AWS Home Lab

https://detectionlab.network/deployment/aws/

## Prerequisites 
- Terraform
- An AWS account
- AWS CLI
- An IAM user and role for Terraform
  - An AWS keypair for that user
  - In the AWS CLI (MacBook)
1. Create user

        aws iam create-user --user-name terra-aws
2. Create policy

        nano ~/assume-role-policy.json
3. Save the policy rules when nano is opened and save
        
        {
          "Version": "2012-10-17",
          "Statement": [
            {
              "Effect": "Allow",
              "Principal": {
                "Service": "cloudformation.amazonaws.com"
              },
              "Action": "sts:AssumeRole"
            }
          ]
        }

4. Create role
   
        aws iam create-role --role-name terraform-role --assume-role-policy-document file://~/assume-role-policy.json

5. Create key pair and save in a secure locate
   
        aws ec2 create-key-pair --key-name <key-pair-name>

6. Add the following permission to the user who will be using terraform
   - https://gist.github.com/clong/5eae6a83e6484bb2c01fa5e9cc6e8c9d

7. Configure the AWS command line utility and set up a profile for Terraform via

       aws configure --profile terraform

8. Create a private/public keypair to use to SSH into logger:

        ssh-keygen -b 4096 -f ~/.ssh/id_logger


