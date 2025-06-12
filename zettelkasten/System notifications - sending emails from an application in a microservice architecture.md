#public
Sending emails programmatically is straight forward. There are many libs and tools, that do this. E.g. there is swaks - the smtp swiss army knife - with which an email can simply be sent as follows (example is based specifically for mailgun):
```
swaks --to <recipient>@gmail.com \
      --from git@homelab.lan \
      --server smtp.mailgun.org:587 \
      --auth LOGIN \
      --auth-user 'postmaster@sandbox<sandbox-id>.mailgun.org' \
      --auth-password '<password-by-mailgun>' \
      --data "Subject: Test Email from Mailgun\n\nHello, this is a test email sent from the terminal."
```
It would be straight forward to simply implement email sending for each microservice of an application. But I don't like the idea of distributing this. 
### Email Service
A much cleaner approach from my perspective is to apply an SMTP relay like [[Postfix - mail transfer agent]] which handles a low of things like queuing undelivered mails and resending them etc. 
It might also be a good idea implement the interface to Postfix on your own. E.g. you might want to implement an Email Service, that receives email requests via a message broker like [[Apache Active MQ Artemis]] with a self-defined message-payload format. 

### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

