# Lambda VPC spot NAT

This is a sample AWS SAM template to demonstrate a Lambda setup in a VPC. Due to high Gateway costs, this implementation try to use spot instances (lowering the service HA) but minimizing its fixed expenditures.

## Requirements

* AWS CLI already configured with Administrator permission

## Setup process

### Installing dependencies

In this example we use `npm` but you can use `yarn` if you prefer to manage NodeJS dependencies:

```bash
cd hello_world
npm install
cd ../
```

### Setup the application

**Packaging SAM application**

```bash
sam package \
    --template-file template.yaml \
    --output-template-file packaged.yaml \
    --s3-bucket REPLACE_THIS_WITH_YOUR_S3_BUCKET_NAME
```

If the previous command ran successfully you should now be able to deploy the application.

**Deploy SAM application**

You can use the AWS CLI to deploy the stack:
```bash
sam deploy \
    --template-file packaged.yaml \
    --stack-name sam-app \
    --capabilities CAPABILITY_IAM \
    --parameter-overrides EnvironmentName=YOUR_ENV_NAME KeyName=YOUR_KEYPAIR_NAME
```
or you can use the AWS Console, loading file `packaged.yaml`
