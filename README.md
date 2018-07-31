# wordpress-demo 
It will deploy wordpress app in kubernetes using helm and jenkins. 

## Docker file

Wordpress offcial docker image is used for this demo. This file will pull the wordpress image and take apt update.

## Jenkins file

This will be used by jenkins pipeline job to run the build.

## helm chart

It will create deployment, service and ingress k8s resources.
