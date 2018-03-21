# week 11 March 21 2018

## agenda
- twilio

## twilio

[twilio](https://www.twilio.com/)

twilio offers a range of services, but today we are going to look at
programmable SMS [twilio sms](https://www.twilio.com/sms). Specifically we are
only going to look at how to send an outbound message.

first thing you will need to do is create a free account with twilio. This is
pretty easy and we won't be going over how to do this in class.

after this create a project, like anything else, give it a logical name, like
wmdd4999test.

After this you will need to get a number from twilio. From within your projects
dashboard select the 'Buy a Number' option under the Phone Numbers panel. search
for a 604 or 778 number for the greater Vancouver area and select a number, it really doesn't matter which number.

Now you should have three things: A phone number, an SID and a token. This is
all that you need to get started.

sample code:

```javascript
// Twilio Credentials
const accountSid = 'your_account_SID'
const authToken = 'your_auth_token'

// require the Twilio module and create a REST client
const client = require('twilio')(accountSid, authToken)

client.messages.create(
  {
    to: '+15558675310',
    from: '+15017122661',
    body: 'This is the ship that made the Kessel Run in fourteen parsecs?',
  },
  (err, message) => {
    console.log(message.sid)
  }
)
```


