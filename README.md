
```````````dotnetcli

$ dotnet new sln

$ dotnet new webapi -o webapi

$ dotnet sln add .\webapi\webapi.csproj

$ dotnet build

$ dotnet run --project .\webApi

curl 'GET' 'http://localhost:5130/weatherforecast' -H 'accept: application/json'
$ curl --get http://localhost:5130/weatherforecast 


# docker support
$ dotnet add ./webapi package Microsoft.NET.Build.Containers

# publish your project for linux-x64
$ dotnet publish --os linux --arch x64 -c Release -p:PublishProfile=DefaultContainer
$ docker image list

# run your app using the new container
$ docker run -it --rm -p 8080:8080 --name mycontainer webapi:latest

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

```
