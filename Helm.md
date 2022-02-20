# Helm

There is three important concepts for Helm : 
1. chart : bundle of information necessary to create an instance of kubernetes application
2. config : configuration information to be merged into a packaged chart to create releasable object
3. release : is a running instance of a chart combined with a specific config

### chart
chart contains :
1. Chart.yaml : information about chart
2. values.yaml : default configuration values of this chart

Example :  
chart to deploy simple spring boot application:

in chart.yml : 
<pre>
apiVersion: v2
name: springboot
description: A Helm chart for Kubernetes
version: 0.1.0
appVersion: "1.16.0"
</pre>

## Helm client
with helm client we can :
1. create local chart development
2. manage repositories
3. manage releases
4. interfacing with the helm library (send charts to be installed,  request for upgrading or uninstalling of existing releases)



