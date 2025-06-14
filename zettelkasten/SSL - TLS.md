---
created: 2025-03-03T08:00
updated: 2025-06-14T21:38
---
#public 
SSL/TLS is used to provide a secure connection between a client and a server. 

### Key elements
##### Authentication
The server sends a certificate to the client. The client can use this to authenticate the server at a well-known certificate authority (CA). See [[Authentication and authorization]]

##### Encryption
private-/public-keys are used to encrypt any communication between the client and the server

##### Integrity
Every transmission is provided with a hash, that only maps to the transmission, if it wasn't manipulated. Using HMAC it is ensured, that the hash isn't manipulated.


### Related Links
- [[SSL - TLS - Handshake]]
- [[SSL - TLS - Ways to set up SSL for a domain]]
### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

