#kubedockerdemo

JUST DOCKER....


BUILD DOCKER V1

docker build -t msauve/mynode:v1 node-demo

RUN DOCKER v1

docker run -d -p 8000:8000 msauve/mynode:v1
curl http://ip:8000

>>>  HELLO Host/Pod: 854d1f444118 



"SCALE"

docker run -d -p 8001:8000 msauve/mynode:v1
docker run -d -p 8002:8000 msauve/mynode:v1
docker run -d -p 8002:8000 msauve/mynode:v1

curl http://ip:8001 ...

STOP ALL CONTAINERS

for example: 

docker stop 854d1f444118
docker rm 854d1f444118

ADD KUBERNETES....

create namespace:
kubectl create -f yaml/kubedemo-namespace.yaml

create replication controller:
kubectl create -f yaml/rc.yaml --namespace kubedemo --validate=falsc

some operations you can demo:
kubectl get rc --namespace kubedemo
kubectl get pods --namespace kubedemo

kubectl scale rc mynode --namespace kubedemo --replicas 5

BUILD DOCKER CONTAINER v2:

edit node-demo/hello-https.js and change message to message of your choice.
docker build -t msauve/mynode:v2 node-demo


In a separate shell, start: watch_update.sh
 
perform rolling deploy:

kubectl --namespace=kubedemo rolling-update mynode --image=msauve/mynode:v2 --update-period=3s

