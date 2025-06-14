---
created: 2025-03-03T08:00
updated: 2025-06-14T21:38
---
#public
It is often required to not also deploy a helm chart, but to also make changes to it. This page describes how to apply the modifications with flux.

In this tutorial, values in the configmap are overwritten by values in the helm-release. This is done by referencing the value with a variable


### Tutorial
##### Add configmap with var for index.html
In the chart templates directory, create a new configmap.yaml file and add the

following:
```yaml
apiVersion: v1  
kind: ConfigMap  
metadata:  
  name: {{ .Release.Name }}-index-html # the name of the config map is the name of the release  
data:  
  # the index.html file is defined in the values.yaml file  
  index.html: |  
    {{ .Values.indexHTML | indent 4 }}
```

##### Add volume to deployment 
Now we modify the container in the deployment. The `deployment.yaml` uses variables, that are read from values.yaml. Here, add the volume and a volumeMount. *(Alternatively, these values can also be set in the values.yaml with a reference in `deployment.yaml`.*
```yaml
# Additional volumes on the output Deployment definition.  
volumes:  
    - name: html  
      configMap:  
        name: {{ .Release.Name }}-index-html  
# Additional volumeMounts on the output Deployment definition.  
volumeMounts:  
  - name: html  
    mountPath: "/usr/share/nginx/html"
```



### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

