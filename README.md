# 100 Days of Clouds with KodeKloud - Days 01 - 10



## Day 4: Enable Versioning for S3 Bucket


## Day 3: Create Subnet



```
aws ec2 describe-vpcs | grep VpcId
```

```
aws ec2 create-subnet \
--cidr-block "172.31.96.0/24" \
--vpc-id "vpc-08c8ae5debbfef1b1" \
--tag-specifications "ResourceType=subnet,Tags=[{Key=Name,Value=xfusion-subnet}]"
```

```
aws ec2 describe-subnets
```

## Day 2: Create a Security Group

Lets make this interesting. I'm going to do everything from the AWS CLI. The point of this lab was to create a security group with a specific name, description, and two inbound rules (one for HTTP and SSH). I found all of this syntax on the AWS website. I realized most of this was supposed to be strings so I added the quotation marks. AI informed me I needed the VPC ID so we queried for that. The one thing I was missing that AWS didnt include was that I needed to put `ec2` after `aws` since security groups are an EC2 resource. Once I ran these 3 commands, I recieved output verifying that the resources were created. 

```
aws ec2 create-security-group \
--description "Security group for Nautilus App Servers" \
--group-name "datacenter-sg" \
--vpc-id "vpc-0e0351f64b8501eeb"
```

```
aws ec2 authorize-security-group-ingress \
--group-name "datacenter-sg" \
--protocol "tcp" \
--port "80" \
--cidr "0.0.0.0/0"
```

```
aws ec2 authorize-security-group-ingress \
--group-name "datacenter-sg" \
--protocol "tcp" \
--port "22" \
--cidr "0.0.0.0/0" 
```


## Day 1: Create Key Pair

For the
