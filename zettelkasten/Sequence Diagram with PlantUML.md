---
created: 2025-03-03T08:00
updated: 2025-06-14T21:38
---
#public
```plantuml
@startuml

autonumber

activate User

User -> "Service" as service : doSomething()
activate service
service -> "service DB" as service_DB: store()
activate service_DB
service_DB -> service: done
deactivate service_DB

@enduml
```

### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

