# week 04 January 24 2018

## agenda
- inserting data into a DynamoDB table using lambda
  - creating a table in DynamoDB
  - creating a new Role and attaching a policy using IAM



## DynamoDB

[quick start guide](https://aws.amazon.com/getting-started/tutorials/create-nosql-table/)

## Writing to a DynamoDB table with Lambda

[aws-sdk dynamodb document client examples](https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/dynamodb-example-document-client.html)

the lambda function code

```javascript
const AWS = require('aws-sdk')
const docClient = new AWS.DynamoDB.DocumentClient({region: "us-west-2"})

exports.handler = (event, context, callback) => {
  
  const newEntry = event.newItem
  
  docClient.put(newEntry, function(err, data){
      if(err) {
          callback(err, null)
      } else {
          callback(null, data)
      }
  })
}
```

the test

```json
{
    "newItem": {
        "Item": {
            "id": "two",
            "message": "hello"
        },
        "TableName": "dynamoDBTest"
    }
}
```
