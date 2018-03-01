# week 08 February 28 2018

## agenda
- environment variables in your serverless.yml  
upcoming:
- working with S3
- third party API/services twilio

## environment variables serverless

the serverless framework has a few different methods for handling environment
variables, we will look at some of them today. generally environment variables with serverless match the pattern ${variable, default} 
allowing you to assign a default value to a variable. This is particularly
useful for variables passed to a service via the CLI.

### using an external file

often you will need to store environment variables, API keys... that you don't
want to include directly in your code. AWS and the serverless framework both
have simple methods for creating and using environment variables.

I will often create an env.yml file to store variables.

```yaml
#variables
dev:
  VarOne: 'my first var'
  VarTwo: 'my second var'
prod:
  ProdVar: 'for production'
```

in the above example you can see how you can store different variables for
different stages of production. To use your variables in your serverless.yml and
in your code first add it to an 'environment' section under 'provider' in your
serverless.yml

```yaml
provider:
  name: aws
  runtime: nodejs6.10
  stage: dev
  region: us-west-2
  environment:
    VarOne: ${file(./env.yml):dev.VarOne}
    VarTwo: ${file(./env.yml):dev.VarTwo}
```

and finally from within your code you can access your environment in objects or
with a new variable.

```javascript
const varOne = process.env.VarOne

const obj = {
  varTwo: process.env.VarTwo
}
```

environment variables can also be added to a function in your serverless.yml
file. When added to a function they are only available to that function.

### self

you may have seen something like this `${self:custom.apiKey}` in some of the example code we have looked
at in class. Rather than an external file, self, points to well, it self.

```yaml
custom:
  apiKey: some-key

function:
  handler: index.hello
  environment:
    apiKey: ${self.custom.apiKey}
```

### opt

opt, or optional variables passed from the CLI

another environment variable you may have encountered in the examples uses
`${opt:stage}`. this allows you to pass different environment variables for
different stages. This is handy for things like a testing stage that might have
a testing database.

```yaml
provider:
  name: aws
  stage: ${opt:stage, 'dev'}
  environment:
    MY_SECRET: ${file(../config.${self:provider.stage}.json):CREDS}
```

entering `sls deploy --stage test` will then use your testing config file
'config.testing.json'

[official docs](https://serverless.com/framework/docs/providers/aws/guide/variables/)
