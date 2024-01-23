
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
```
