---
created: 2025-04-04T09:01
updated: 2025-06-12T23:45
---
#public 

##### Clear handshake overview
![[EFALGyFXsAA92Tq.jpg]]

##### Detailed handshake
The following graph includes 
- authentication with CA
- Details on how SESSION MASTER KEY is created. It includes random numbers RAND-SERVER and RAND-CLIENT, that are used together with PRE-MASTER. By including these random numbers, it is ensured, that the SESSION MASTER KEY can only be used for this unique session. 

```plantuml
activate Client
activate Server
activate CA

Client -> Server : \
- client says hello with <color:orange>RAND-CLIENT</color> \n\
- sends TLS version \n\
- sends <color:Salmon>cipher suits</color>, available to the client

Server -> Client : \
- returns <color:purple>RAND-SERVER</color> \n\
- returns accepted <color:Salmon>cipher suit</color> \n\
- returns <color:cyan>CERTIFICATE</color> for authentication \n\
- returns <color:brown>SERVERS PUBLIC KEY</color>

Client -> CA : \
sends <color:cyan>CERTIFICATE</color> for authentication

CA -> Client : \
- sends ACKs for certificate \n\
- ACK is encrypted with <color:DarkGreen>CAs PRIVATE KEY</color>

Client -> Client : \
decrypts ACK with <color:DarkGreen>CAs PUBLIC KEY</color>, \n\
which is stored on the local nmachine, managed by operating system or browser, \n\
and protected with root rights

Client -> Server : \
sends a new random value <color:Crimson>PRE-MASTER</color>, \n\
which is encrypted using <color:brown>SERVERS PUBLIC KEY</color> 

Client -> Client : \
creates <color:ForestGreen>SESSION MASTER KEY</color> \n\
using <color:orange>RAND-CLIENT</color>, <color:Crimson>PRE-MASTER</color> and <color:purple>RAND-SERVER</color>
deactivate Client
deactivate CA
deactivate Server

Server -> Server : \
creates <color:ForestGreen>SESSION MASTER KEY</color> \n\
using <color:orange>RAND-CLIENT</color>, <color:Crimson>PRE-MASTER</color> and <color:purple>RAND-SERVER</color>

Client -> Server : \
sends test message using <color:ForestGreen>SESSION MASTER KEY</color>

Server -> Client : \
- decrypts message using  <color:ForestGreen>SESSION MASTER KEY</color> \n\
- returns ACK, encrypted using <color:ForestGreen>SESSION MASTER KEY</color>

Client -> Server : \
- starts sending actual requests, encrypted using <color:ForestGreen>SESSION MASTER KEY</color>
deactivate Client
deactivate CA
deactivate Server
```


### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

