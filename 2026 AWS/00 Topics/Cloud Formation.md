
* Cloud formation is checklist that will used to create the aws infra
* generally we will write the instruction in yaml file
* Template --> yaml file --> instruction for infra build. we will write what we want
* Stack --> Template when given to aws will create the stack. it's running version of template
* Nested stack: Big template is hard to manage so will spilt as per the department
	* Like:
		* network.yaml
		* compute.yaml
		* database.yaml
		* security.yaml
	* One root stack call all of them

### Sample CloudFormation template: 5 sections

```
AWSTemplateFormatVersion: "2010-09-09"
Description: "PayFlow shield - Netwrok stack"

Parameters:
	Enviornment:
		Type: String
		AllowedValues: [dev,staging,prod]

Resources:
	MYVPC: 
	Type: AWS::EC2::VPC
	Properties:
	   CidrBlock: 10.0.0.0/16
	   Tags:
	      - Key: Name
	        Value: payflow-vpc
	        
Outputs:
	VPCId:
	   Value: !Ref MyVPC
	   Export:
		   Name: PayFlow-VPC-ID

```

#### Deployment Command:

```
aws cloudformation deploy \
	-- template-file root-stack.yaml \
	-- stack-name payflow-shield-dev
	-- parameter-overrides Environment=dev \
	-- capabilities CAPABILITY_NAMED_IAM \
	-- region ap-south-1
```

