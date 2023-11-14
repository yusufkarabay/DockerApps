FROM mcr.microsoft.com/dotnet/sdk:7.0 as build
WORKDIR /app
COPY *.csproj .
RUN dotnet restore
COPY . .
RUN dotnet publish DockerWebApp.csproj -c Release -o out


FROM mcr.microsoft.com/dotnet/aspnet:7.0 
WORKDIR /app
COPY --from=build /app/out .
ENV ASPNETCORE_URLS="http://*:4500"
ENV ASPNETCORE_ENVIRONMENT="Development"
ENTRYPOINT ["dotnet", "DockerWebApp.dll"]