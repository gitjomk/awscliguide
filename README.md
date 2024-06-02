# awscliguide
AWS CLI guide

# Check available AWS VPCs in a specific region

aws ec2 describe-vpcs --region us-east-1

# Create a new AWS VPC in a specific region
# aws ec2 create-vpc --cidr-block [didr block] --region [region name]

aws ec2 create-vpc --cidr-block 20.0.0.0/16 --region us-east-1

# Create a tag for the VPC 
# aws ec2 create-tags --resources [resource-id] --tags key=Name,value=[NameOfResource]
aws ec2 create-tags --resources vpc-xxxxxxxxxxxx --tags Key=Name,Value=awscli-vpc

# Create Internet gateway in a specific region 
aws ec2 create-internet-gateway --region us-east-1

# Create a tag for the Internet gateway
aws ec2 create-tags --resources igw-xxxxxxxxxxxx --tags Key=Name,Value=awscli-igw


