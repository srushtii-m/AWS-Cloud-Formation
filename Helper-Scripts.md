## Helper Scripts

Helper scripts are a set of Python scripts provided by AWS that assist in the installation, configuration, and signaling of application resources within CloudFormation stacks.   

Useful when deploying and managing AWS resources with EC2 instances and are commonly used in conjunction with AWS CloudFormation's AWS::CloudFormation::Init metadata key.     

The four primary helper scripts are cfn-init, cfn-signal, cfn-get-metadata, and cfn-hup.    

1. cfn-init    
Used to retrieve and interpret resource metadata, install packages, create files, and start services specified in the AWS::CloudFormation::Init metadata block.      

2. cfn-signal     
Used to signal AWS CloudFormation to indicate whether EC2 instances have been successfully created or updated. It is often used in conjunction with the CreationPolicy or UpdatePolicy attributes to prevent the stack's creation process from proceeding before resources are fully configured.   

3. cfn-get-metadata    
Used to retrieve metadata for a resource or path specified in the AWS::CloudFormation::Init metadata key.  

4. cfn-hup     
Used to check for updates to metadata and execute custom hooks when changes are detected.    