## this page is for building .net docker images..

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
RUN mkdir app
COPY docker-guide/dist/* /app/
EXPOSE 80
ENTRYPOINT ["dotnet", "/app/docker-guide.dll"]
```
