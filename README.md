CREATE NAMESPACE:

kubectl create -f kubemo-namespace.yaml

BUILD DOCKER V1

docker build -t msauve/mynode:v1 node-demo

RUN DOCKER v1

docker run -d -p 8000:8000 msauve/mynode:v1
curl http://ip:8000

"SCALE"

docker run -d -p 8001:8000 msauve/mynode:v1
docker run -d -p 8002:8000 msauve/mynode:v1
docker run -d -p 8002:8000 msauve/mynode:v1

curl http://ip:8001 ...



kubectl --namespace=kubedemo rolling-update mynode --image=msauve/mynode:v2 --update-period=3s




# kubedockerdemo
