# Cloud formations

This section contains various Cloud Formation templates, using the `yaml` template engine, which can be run on your own AWS account, to quickly build up one or more services and configurations.

# Structure of the Repository

This repository is divided into two main sections:

- `services`: contains various templates which enable various services, in different flavours.
- `architectures`: contains various templates which allow you to deploy more complex architectures into a single cloud formation.

## How to run a Template

1. Open the Console and Login with your AWS Account<br />
`aws configure`
2. Deploy a template using AWS CLI<br />
`aws cloudformation deploy --template-file .\template.yaml --stack-name name --parameter-overrides "Param1=Value1"` 

Templates provides output parameters, which can be used to identify the template, for example, or to directly access the resource.

 > **Beware** <br />
 My templates **do not have** the parameter `DeletionPolicy: Retain`. So, if you delete the Stack, all resources beneat will be gone too.

By using `aws deploy`, you will automatically create incremental changesets inside your Cloud Stack Formation, which allows you to track the incremental changes applied to your resources.

## How to concat multiple Stack(s) together

You might come up with scenarios where you want to concat multiple Cloud Stack together. For example, you will need to generate a CMK (Custom Managed Key) in order to encrypt an S3 storage.