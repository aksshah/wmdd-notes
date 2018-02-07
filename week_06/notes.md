# week 06 February 07 2018

## agenda
- using resources with the serverless framework
- installing modules for a serverless application

## adding resources

Last week you were introduced to the serverless framework and the serverless.yml
file that is used to configure an API created with serverless. This week we are
going to look at how to add resources(DynamoDB, S3 Bucket...) to our API.

Resources can be added using the serverless.yml file under the resources
section. Today we will specifically look at creating a DynamoDB table as a
resource.

In addition to creating a resources section in the serverless.yml file we need
to install the aws-sdk module and create a policies to allow our function to
access the resource. first let's look at installing modules.

### installing a module with AWS and serverless is no different than any other
node project. `npm i aws-sdk -S` done! 

### resources

the following is an example from the serverless docs.

```yaml
# serverless.yml

resources:  // CloudFormation template syntax
  Resources:
    usersTable:
      Type: AWS::DynamoDB::Table
      Properties:
        TableName: usersTable
        AttributeDefinitions:
          - AttributeName: email
            AttributeType: S
        KeySchema:
          - AttributeName: email
            KeyType: HASH
        ProvisionedThroughput:
          ReadCapacityUnits: 1
          WriteCapacityUnits: 1
```

### policies

under the provider section of the server
you can add an IAM role statements section where you can define the permissions
you want your service to have.

```yaml
  iamRoleStatements:
    - Effect: Allow
      Action:
        - dynamodb:Query
        - dynamodb:Scan
        - dynamodb:GetItem
        - dynamodb:PutItem
        - dynamodb:UpdateItem
        - dynamodb:DeleteItem
      Resource: "arn:aws:dynamodb:us-west-2:*:*"
```

## additional resources

[vidoe tutorial](https://serverless.com/blog/build-a-serverless-rest-api/)

##assignment 2, Recipes API

Using what you have learned about AWS and the serverless framework create the
backend for an app that allows you to store, update, read and delete recipes.

Your API should use DynamoDB as a database.

### submission guidelines

using the D2L submission folder for assignment 2, submit a .txt file with the
following:  
- a link to your projects code on GitHub
- instructions for testing your API
- URLs for:
  - Creating a recipe
  - Reading a recipe
  - Deleting a recipe
  - Updating a recipe

you can use any tool that you like for testing your API but I recommend Curl,
Httpie or postman, since these have been discussed in a previous class.

### Due date

February 14 14:30
