## this page is for building .net docker images..

## how to install .net in Ubuntu 20.x
```
 wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
 sudo dpkg -i packages-microsoft-prod.deb
 rm packages-microsoft-prod.deb
 apt-get update &&   sudo apt-get install -y dotnet-sdk-6.0
 sudo apt-get install -y dotnet-runtime-7.0
 sudo apt-get remove -y dotnet-runtime-7.0
 sudo apt-get install -y dotnet-runtime-6.0
```
## Create project.
```
root@ubansinode1:~# dotnet new mvc --name first-web-app

Welcome to .NET 6.0!
---------------------
SDK Version: 6.0.411

Telemetry
---------
The .NET tools collect usage data in order to help us improve your experience. It is collected by Microsoft and shared with the community. You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry

----------------
Installed an ASP.NET Core HTTPS development certificate.
To trust the certificate run 'dotnet dev-certs https --trust' (Windows and macOS only).
Learn about HTTPS: https://aka.ms/dotnet-https
----------------
Write your first app: https://aka.ms/dotnet-hello-world
Find out what's new: https://aka.ms/dotnet-whats-new
Explore documentation: https://aka.ms/dotnet-docs
Report issues and find source on GitHub: https://github.com/dotnet/core
Use 'dotnet --help' to see available commands or visit: https://aka.ms/dotnet-cli
--------------------------------------------------------------------------------------
The template "ASP.NET Core Web App (Model-View-Controller)" was created successfully.
This template contains technologies from parties other than Microsoft, see https://aka.ms/aspnetcore/6.0-third-party-notices for details.

Processing post-creation actions...
Running 'dotnet restore' on /root/first-web-app/first-web-app.csproj...
  Determining projects to restore...
  Restored /root/first-web-app/first-web-app.csproj (in 280 ms).
Restore succeeded.
```
## publish
```
root@ubansinode1:~/first-web-app# dotnet publish -o pub
MSBuild version 17.3.2+561848881 for .NET
  Determining projects to restore...
  All projects are up-to-date for restore.
  first-web-app -> /root/first-web-app/bin/Debug/net6.0/first-web-app.dll
  first-web-app -> /root/first-web-app/pub/

cd pub
zip -r site.zip *
```
## Push to Azure
```
az webapp deployment source config-zip \
    --src site.zip \
    --resource-group [sandbox resource group name] \
    --name <your-app-name>
```

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
RUN mkdir app
COPY docker-guide/dist/* /app/
EXPOSE 80
ENTRYPOINT ["dotnet", "/app/docker-guide.dll"]
```

```
docker run -it --rm -p 8090:80 --name aspnetcore_sample mcr.microsoft.com/dotnet/samples:aspnetapp
```
