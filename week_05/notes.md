# week 05 January 31 2018

## agenda
- intro to serverless framework
  - installing serverless CLI
  - provider credentials
  - serverless.yml

## serverless framework

The serverless framework is a toolkit for quickly building serverless
apps using a variety of platforms and programming languages. We are going to
stick with AWS and NodeJS for the remainder of the class.

[serverless framework site](https://serverless.com/)

### getting setup

the serverless CLI is distributed as a Node module so installing it is just like
installing any other node module. `npm i -g serverless` this will install the
serverless framework globally, you can also install to local directory and save
it as a dev dependency.

before jumping into using the serverless CLI you need to setup provider
credentials. This gives serverless permission and keys to actually access aws
tools.

1) log into your aws account and go to the IAM console.

2)select users, then the big blue add user button, I generally call this user
something like serverlessFrame, but you can give your new user any name you
want. when performing this step be sure to select the 'programmatic access'
check box under 'Select AWS access type' this will generate two keys that you
will need for later.

3) copy and paste your access key and secret access key somewhere, or download
them (aws generates a csv file for you).

4)add permissions, select your new user name then the 'Permissions' button.
click the 'Attach Policy' button then attach 'AdministratorAccess'

5) using the serverless CLI you can create your AWS credentials. enter  
`sls config credentials --provider aws --key your_key --secret your_secret_key`  
this creates an .aws directory (in your home directory on a unix like machine) with a credentials file that stores your
credentials. Assuming that everything went well you are ready to start using the
serverless framework.

once serverless is installed and you have setup provider credentials you can create a new project with the CLI.  
`sls create -t aws-nodejs -p first_serverless`  
`-t` specifies a template, in this case AWS using NodeJS.  
`-p` specifies a file path

this creates two important files for us, the handler.js and serverless.yml
files. the handler.js file probably doesn't contain anything new to any of you
at this point, so we will focus on the serverless.yml file.

## serverless.yml

there is a lot of content commented out by default in your serverless.yml file
and we will come back and look at some of it a little later, for now we are just
going to look at the basics.

```yaml
service: slsdemo

provider:
  name: aws
  runtime: nodejs6.10
  region: us-west-2

functions:
  hello:
    handler: handler.hello
    events:
      - http:
          path: hello
          method: get
```
[yaml](http://www.yaml.org/)

## getting your function online

when you have edited your function(s) and serverless.yml and you are ready to
deploy, `sls deploy`. this will take a little while the first time you run it,
and if everything worked you should see an endpoint, simply copy and paste this
into your browser

## testing

to run a function locally `sls invoke -f hello -l`

## removing

if you want to remove a service `sls remove` this is particularly handy when you
are learning and using the aws free tier
