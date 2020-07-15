# dotnet-amqp  Producer using AMQP client
.NET Core AMQP Producer 

### Steps to deploy on Openshift

## Login to openshift using oc client.
oc login OpenshiftAPIURL.

## Import dot net core image

oc import-image dotnet/dotnet-21-rhel7 --from=registry.access.redhat.com/dotnet/dotnet-21-rhel7 --confirm

## Create a new build
oc new-build --binary=true --image-stream=dotnet-21-rhel7  --name=netamqpproducer 

## Start the Build poiting the --from-dir= to the dotnet-amqp project source
oc start-build netamqpproducer --from-dir=. --follow

## Create a new app using the build
oc new-app netamqpproducer

