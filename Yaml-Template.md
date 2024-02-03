## Cloud Formation templates (YAML or JSON) sets up an EC2 instance or S3 bucket or any other AWS resources 

## Template:

AWSTemplateFormatVersion: '2010-09-09'
Description: A basic CloudFormation template for creating an EC2 instance and an S3 bucket.

Parameters:
  InstanceType:
    Description: EC2 instance type
    Type: String
    Default: t2.micro
    AllowedValues:
      - t2.micro
      - t2.small
      - t2.medium
    ConstraintDescription: must be a valid EC2 instance type.

  KeyName:
    Description: Name of an existing EC2 KeyPair to enable SSH access to the instance
    Type: AWS::EC2::KeyPair::KeyName
    ConstraintDescription: must be the name of an existing EC2 KeyPair.

  BucketName:
    Description: Name of the S3 bucket to create
    Type: String
    Default: MyS3Bucket

Resources:
  MyEC2Instance:
    Type: AWS::EC2::Instance
    Properties:
      InstanceType: !Ref InstanceType
      KeyName: !Ref KeyName
      ImageId: ami-0abcdef1234567890 # Replace with the correct AMI for your region
      SecurityGroups:
        - !Ref InstanceSecurityGroup

  InstanceSecurityGroup:
    Type: AWS::EC2::SecurityGroup
    Properties:
      GroupDescription: Enable SSH access via port 22
      SecurityGroupIngress:
        - IpProtocol: tcp
          FromPort: '22'
          ToPort: '22'
          CidrIp: 0.0.0.0/0 # Caution: This is open to the world. For production, restrict the IP range.

  MyS3Bucket:
    Type: AWS::S3::Bucket
    Properties:
      BucketName: !Ref BucketName
      AccessControl: Private

Outputs:
  InstanceID:
    Description: The Instance ID of the EC2 instance
    Value: !Ref MyEC2Instance

  InstancePublicIP:
    Description: The public IP address of the EC2 instance
    Value: !GetAtt MyEC2Instance.PublicIp

  BucketName:
    Description: The name of the S3 bucket
    Value: !Ref MyS3Bucket
