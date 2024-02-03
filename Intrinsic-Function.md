## Intrinsic Functions

Intrinsic functions are special actions that process data passed to them and return the result.   

They enable us to assign values to properties that are not available until runtime.   

CloudFormation provides intrinsic functions such as Ref and Fn::GetAtt:  

Ref can be used to retrieve the logical ID of a resource or the value of a parameter.    

Fn::GetAtt can be used to retrieve the value of a resource attribute that is not known until runtime.   

Resources:
  MyEC2Instance:
    Type: 'AWS::EC2::Instance'
    Properties:
      # ...

Outputs:
  InstanceId:
    Description: "The Instance ID of the EC2 instance"
    Value: !Ref MyEC2Instance

  InstancePublicIP:
    Description: "The public IP address of the EC2 instance"
    Value: !GetAtt MyEC2Instance.PublicIp




