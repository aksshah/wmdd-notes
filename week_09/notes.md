# week 09, march 07 2018

## agenda 
- events
- S3
- Cron

## s3

setting up an S3 bucket with the Serverless framework is a lot like setting up a
DynamoDB table.

```yaml
service: s3_fetch

custom:
  bucket: myBucket

provider:
  name: aws
  runtime: nodejs6.10
  stage: dev
  region: us-west-2
  iamRoleStatements:
    - Effect: Allow
      Action:
        - s3:PutObject
      Resource: "*"

functions:
  postprocess:
    handler: handler.postprocess
    events:
      - s3:
          bucket: ${self:custom.bucket}
          event: s3:ObjectCreated:*
          rules:
            - suffix: .png
```

the above serverless.yml will create an S3 bucket (named myBucket) that will allow you to add
objects to it.

[complete Serverless example project](https://github.com/serverless/examples/tree/master/aws-node-upload-to-s3-and-postprocess)

## cron

There will come a time when you want a function to run at a specified time. 
If you pause to think about this I am sure that you can come up with several use cases for this.
In computer science and software development you will often here this referred to as a 'Cron job'. 
'Cron' is a utility for scheduling jobs at timed intervals that comes with UNIX like operating systems and dates back
to the early days of UNIX.

The Serverless frame work and AWS make calling a function at a specified time very easy to setup. To set up a 
function that runs at a specified time you really only need to add one thing to your serverless.yml file, a schedule.

```yaml
functions:
  cron:
    handler: handler.hello
    events:
      - schedule: rate(1 day)
```

The above serverless.yml  would set up a scheduled event that runs once a day.

(1 minute) every minute, (7 days) every 7 days... you get the idea.

[more on AWS rates](http://docs.aws.amazon.com/AmazonCloudWatch/latest/events/ScheduledEvents.html#RateExpressions)
[more on formatting times](http://docs.aws.amazon.com/lambda/latest/dg/tutorial-scheduled-events-schedule-expressions.html)

