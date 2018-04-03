# take home exam wmdd 4999

## Short Answer questions

### 1 messages

Research and write about 2 paragraphs describing how you could use the AWS tools
SNS and SQS to aide in handling messages between services in a microservices
architecture.

### 2 frameworks

Research two alternative frameworks to the Serverless framework that we looked
at in class. These should be frameworks for working with microservices and
serverless(the architecture not the framework). Write about 2 paragraphs on each
of them. What do they offer, if anything that is different from the Serverless
framework...?

## small project

Using what you have learned this term about serverless/microservices, the
Serverless framework, and the AWS tools used in class (Lambda, S3, DynamoDB) you
are going to create part of the backend for a streaming music app, similar to
Spotify.

You will code the following microservices(remember that these are functions):

1. A services that adds all of your audio files in an S3 bucket to a DynamoDB
database.

2. A service that allows a user to search for a song(the name of the file) or
returns a list of all of the songs(files) you have in your S3 bucket.

3. A service that allows you to create a new playlist and add a song to that
playlist.(You might want to use a second DynamoDB table for this)

For the purposes of this assignment I recommend making several small txt files
to stand in for your MP3s/OGG(other audio files)

As in the previous project you can add a few files to your S3 bucket using the
AWS web console for testing purposes

## Submission instructions
submit a .txt file in the D2L dropbox with a link to your github repository
as well as the your answers to the short answer questions and any instructions I
might need to test your work.

## Due Date  
Friday April 6, 12:00
