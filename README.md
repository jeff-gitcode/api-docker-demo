
```````````dotnetcli

$ dotnet new sln

$ dotnet new webapi -o webapi

$ dotnet sln add .\webapi\webapi.csproj

$ dotnet build

$ dotnet run --project .\webApi

curl 'GET' 'http://localhost:5130/weatherforecast' -H 'accept: application/json'
$ curl --get http://localhost:5130/weatherforecast 


$ docker image list


# create image
$ docker build -t webapi -f ./webApi/Dockerfile .
$ docker image ls

# create container
$ docker run --name webapi -p 8082:8080 -d webapi:latest
$ docker ps -a
$ docker stop webapi
$ docker rm webapi

$ docker-compose up -d
$ docker-compose stop

# remove git change
$ git rm -r "./webapi/bin/"
$ git rm -r "./webapi/obj/"


# docker support
$ dotnet new webapi -o webapi2
$ dotnet add ./webapi2 package Microsoft.NET.Build.Containers
$ dotnet sln add .\webapi2\webapi2.csproj

$ dotnet build .\webapi2
$ dotnet build api-docker-demo.sln

# publish your project for linux-x64
$ dotnet publish .\webapi2\webapi2.csproj --os linux --arch x64 -c Release -p:PublishProfile=DefaultContainer

# run your app using the new container ?
$ docker run -it --rm -p 8086:8080 --name mycontainer webapi2:latest

# kong & db
$ docker-compose build

$ docker-compose up

$ docker-compose down

# kong
$ curl -Ls https://get.konghq.com/quickstart | bash

 Kong Gateway Ready 🐵

=======================================================
 ⚒️                                           Using Kong
=======================================================

• Kong Data Plane endpoints:
    HTTP  = http://localhost:8000

• This script has written an environment file you can
  source to make connecting to Kong easier. Run this
  command to source these variables into your
  environment:

→ source /tmp/kong/quickstart/kong.env

• Now you can make requests to your Kong Gateway using
  variables from the file, for example:

→ curl -s $KONG_PROXY/mock

=======================================================
 ⚒️                                      Administer Kong
=======================================================

• Kong Admin API endpoint:
   HTTP = http://localhost:8001

• To administer the gateway with curl:

→ curl -s https://localhost:8001

• To stop the gateway run:

→ curl https://get.konghq.com/quickstart | \
    bash -s -- -d -a kong-quickstart

# kong manager
http://localhost:8002/workspaces

# Creating services
$ curl -i -s -X POST http://localhost:8001/services --data name=pet-store --data url="https://petstore.swagger.io/v2"

# view service
$ url -X GET http://localhost:8001/services/pet-store

# listing service
$ curl -X GET http://localhost:8001/services

http://localhost:8002/default/services

# Creating routes
$ curl -i -X POST http://localhost:8001/services/pet-store/routes --data "paths[]=/petstore" --data name=pet-store

$ Viewing route configuration
$ curl -X GET http://localhost:8001/services/pet-store/routes

http://localhost:8002/default/routes

$ curl -X GET http://localhost:8000/petstore/pet/10


//////////////////////////////

# start db
$ docker run -d --name kong-database --network=kong-comic-net -p 5432:5432 -e "POSTGRES_USER=kong" -e "POSTGRES_DB=kong"  -e "POSTGRES_PASSWORD=kong" postgres:9.6

# prepare  db
$ docker run --rm --network=kong-comic-net  -e "KONG_DATABASE=postgres" -e "KONG_PG_HOST=kong-database" -e "KONG_PG_USER=kong" -e "KONG_PG_PASSWORD=kong"  kong:latest kong migrations bootstrap

# start kong
$ docker run -d --name kong --network=kong-comic-net -e "KONG_DATABASE=postgres" -e "KONG_PG_HOST=kong-database" -e "KONG_PG_USER=kong" -e "KONG_PG_PASSWORD=kong" -e "KONG_PROXY_ACCESS_LOG=/dev/stdout"  -e "KONG_ADMIN_ACCESS_LOG=/dev/stdout"      -e "KONG_PROXY_ERROR_LOG=/dev/stderr"      -e "KONG_ADMIN_ERROR_LOG=/dev/stderr"      -e "KONG_ADMIN_LISTEN=0.0.0.0:8001, 0.0.0.0:8444 ssl"      -p 8000:8000      -p 8443:8443     -p 127.0.0.1:8001:8001     -p 127.0.0.1:8444:8444      kong:latest

# verify kong is running
$ curl -i http://localhost:8001/

# expose service through kong
$ curl -i -X POST http://localhost:8001/services --data name=api_demo --data url="http://api_demo:8088/"

# list services
$ curl -X GET http://localhost:8001/services

# add routes
$ curl -i -X POST http://localhost:8001/services/api_demo/routes --data "paths[]=/mock" --data name=api_demo

# listing routes
$ curl http://localhost:8001/routes

http://localhost:8000/mock/weatherforecast
```
