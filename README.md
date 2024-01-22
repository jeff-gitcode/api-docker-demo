
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
$ docker run -it --rm -p 8080:80 --name mycontainer webapi:latest

$ docker ps -a
```
