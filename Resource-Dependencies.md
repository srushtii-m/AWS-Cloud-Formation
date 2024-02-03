## Resource Dependencies

In AWS CloudFormation, resource dependencies are used to specify the creation order of AWS resources in a CloudFormation stack.    

CloudFormation normally creates and deletes resources in parallel to the extent possible, but we can use dependencies to enforce a specific order.    


Ways to Define Dependencies:   

1. DependsOn Attribute:    

The DependsOn attribute in a resource declaration explicitly specifies that the creation of a specific resource follows another. When a DependsOn attribute is added to a resource, it ensures that CloudFormation creates the dependent resource first.    

2. Implicit Dependencies:   

CloudFormation automatically creates implicit dependencies when you refer to other resources in certain properties of a resource. For example, if we use the Ref or Fn::GetAtt functions to refer to another resource, CloudFormation creates an implicit dependency between the two resources.     

