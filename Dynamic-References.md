## Dynamic References

Dynamic references in AWS CloudFormation templates allows to reference values in a template that are only available at runtime.    

These references can point to values stored in AWS Systems Manager Parameter Store or AWS Secrets Manager, enabling the template to dynamically include information that may change over time or should be kept secure.   

Types of Dynamic References:    

1. AWS Systems Manager Parameter Store:       
To reference parameters stored in Systems Manager Parameter Store dynamically.      
Syntax: {{resolve:ssm:parameter-name:version}}      

2. AWS Secrets Manager:       
To reference secrets stored in AWS Secrets Manager.        
Syntax: {{resolve:secretsmanager:secret-name:secret-version:json-key:json-version}}   

