---
created: 2025-03-03T08:00
updated: 2025-06-14T21:38
---
#public
Sometimes I want to check, if a peace of software actually sends http requests. Normally, when I have control over the sender and the receiver, this is quite easy, since I can simply look into the logs.

But sometimes, my peace of software is a blackbox, e.g. a certain dependency, that I included into my application. I may struggle with the configuration, and don't get any logs, and I am not able to see the incoming requests in my receiver. 

I solved this by implementing a little http server with the following properties:
- It accepts all kinds of requests...
- prints them out...
- and returns 200

It is provided as a docker-compose. 

### Github project
[[github - fake server]]

### Integration into envi
In my own shell configuration (dotfiles and so on), the server can be started with the command.

`fake-server <port>`

See my shell configuration here: [[github envi]]


### Related links
- [[Log requests with a proxy]]
- [[chatGPT- nginx request logger]]




### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

