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
aws ec2 create-tags --resources igw-xxxxxxxxxxxx --tags Key=Name,Value=awscli-igw --region us-east-1

# Check the changes of Internet gateway that has been created
aws ec2 describe-internet-gateways --region us-east-1

# Attach the Internet gateway with the VPC
aws ec2 attach-internet-gateway --vpc-id vpc-xxxxxxxxxxxxxx --internet-gateway-id igw-xxxxxxxxxxxxxxxx --region us-east-1

# Create a public subnet 
# aws ec2 create-subnet --vpc-id [VPC id] --availability-zone [availability zone name] --cidr-block [cidr block] --region [retion name]
aws ec2 create-subnet --vpc-id vpc-xxxxxxxxxxxxxxxx --availability-zone us-east-1a --cidr-block 20.0.0.0/24 --region us-east-1

#create a tag for the public subnet
 aws ec2 create-tags --resources subnet-xxxxxxxxxxxxx --tags Key=Name,Value=awscli-pubsubA --region us-east-1

#Check the changes in the created subnet
aws ec2 describe-subnets --subnet-id subnet-xxxxxxxxxxxxx --region us-east-1

#create a routing table for the public subnet
#aws ec2 create-route-table --vpc-id [vpc id] --region [region name]
aws ec2 create-route-table --vpc-id vpc-xxxxxxxxxxxxxx --region us-east-1

#create a tag for the public route
 aws ec2 create-tags --resources rtb-xxxxxxxxxxxxx --tags Key=Name,Value=awscli-pubrtb1

# Create a route in a routing table for the default route 0.0.0.0/0 to use Internet Gateway as a gateway
aws ec2 create-route --route-table-ids rtb-xxxxxxxxxxxxx --destination-cidr-block "0.0.0.0/0" --gateway-id igw-xxxxxxxxxxxxx --region us-east-1

# Check the route talbe that has been craeted
aws ec2 describe-route-tables --route-table-ids rtb-xxxxxxxxxxxxx


