---
created: 2025-03-03T08:00
updated: 2025-06-12T23:45
---
#public


```plantuml
@startuml 
start 
partition Sender { 
	:Kommunikation einer Aussage; 
	#lightgreen :Anpassung an Empfänger;
} 
-> Kommunikation;
partition Empfänger { 
	:Filter durch Erfahrungen, Einflüsse, etc.; 
	#lightgreen :gewünschte Wahrnehmung der Aussage; 
} 

if (happy?) then (true)
	:party;
else (false)
	:sleep;
endif
stop 
@enduml
```


### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

