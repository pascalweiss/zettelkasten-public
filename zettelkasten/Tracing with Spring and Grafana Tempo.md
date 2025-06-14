---
created: 2025-03-03T08:00
updated: 2025-06-14T21:38
---
### Observability
The term stands for "how well you can understand the internals of your system by examining its output".


### Workflow on errors
- Go to Tempo, and search traces with an error. Maybe add some more filters
- Select one of the traces
- find the span with the error
- get the log with the error

### Correlations with Grafana, Loki and Tempo
- Metrics are correlated with traces
- traces are correlated with logs

### Benefits
- Logs that belong to same trace are grouped together
- When you search for an error, you can search by trace, which is much less cluttered
- For each trace and each span, we get the duration. So If something takes very long, we can see it from the trace.
- If fronted receives errors with trace ids (and these are logged in in web analytics, or we show them to the user), then we can quickly find the corresponding error log. 


### Examples
- working docker-compose example. Sets up grafana, tempo, and a full application https://grafana.com/docs/tempo/latest/getting-started/docker-example/

### Useful Links
- Spring docu for tracing: https://docs.spring.io/spring-boot/reference/actuator/tracing.html
- How to by spring.io: https://spring.io/blog/2022/10/12/observability-with-spring-boot-3
- Tutorial about springoot and grafana https://www.springcloud.io/post/2022-11/springboot-grafana/#gsc.tab=0
- How to use micrometer: https://micrometer.io/docs/tracing#_using_micrometer_tracing_directly
- https://spring.io/blog/2024/10/28/lets-use-opentelemetry-with-spring
- Somebody saying, you only need otel https://stackoverflow.com/questions/76664620/what-is-the-purpose-of-micrometer-in-opentelemetry-or-can-opentelementry-add-th
- Example Repos:
	- https://github.com/blueswen/spring-boot-observability
- Micrometer Talk (SpringBoot, Grafana): https://www.youtube.com/watch?v=fh3VbrPvAjg
- comparison micrometer tracing vs otel https://blog.frankel.ch/opentelemetry-tracing-spring-boot/
- https://www.baeldung.com/spring-boot-opentelemetry-setup


### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

