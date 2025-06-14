---
created: 2025-03-03T08:00
updated: 2025-06-14T21:38
---
#public

An open source helm chart repository. It is handy for quickly setting up a helm repository via docker. 

#### Start up ChartMuseum

First, start up a container, and supply a local folder as the volume for the charts (-v). Also we can protect it with password and username (e.g. if there is the goal to experiment with credentials).

```shell
docker run --rm -it \
  -p 8080:8080 \
  -e DEBUG=1 \
  -e STORAGE=local \
  -e STORAGE_LOCAL_ROOTDIR=/charts \
  -e BASIC_AUTH_USER=chartuser \
  -e BASIC_AUTH_PASS=mypass \
  -v $(pwd)/charts:/charts \
  ghcr.io/helm/chartmuseum:v0.16.2
```

#### Create a Helm Chart
Now create a helm chart locally. 
```shell
helm create busybox
```
Edit the deployment so that it does not contain the container ports and also add the container command line arguments:

```yaml
containers:  
  - name: {{ .Chart.Name }}  
    securityContext:  
      {{- toYaml .Values.securityContext | nindent 12 }}  
    image: "{{ .Values.image.repository }}:{{ .Values.image.tag | default .Chart.AppVersion }}"  
    imagePullPolicy: {{ .Values.image.pullPolicy }}  
    command:  
      - sleep  
      - infinity  
    resources:  
      {{- toYaml .Values.resources | nindent 12 }}
```

Modify the values as follows:
```shell
image:  
  repository: busybox  
  # This sets the pull policy for images.  
  pullPolicy: IfNotPresent  
  # Overrides the image tag whose default is the chart appVersion.  
  tag: "latest"
```

#### Package and push the helm chart
Create a helm package
```shel
helm package .
```
and push it to the repo
```shell
curl -u chartuser --data-binary "@busybox-0.1.0.tgz"
```
Now see that it is listed with:
```shell
curl -u chartuser  -X GET http://localhost:8080/api/charts
```
#### Add the repo to the machine
```
helm repo add my-helm-repo --username chartuser
```


### Related Links
- Readme with API description: https://github.com/helm/chartmuseum




### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

