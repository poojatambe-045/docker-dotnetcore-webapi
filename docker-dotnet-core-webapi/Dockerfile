FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build-env
WORKDIR /App

COPY . ./

RUN dotnet restore

RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/aspnet:8.0

WORKDIR /App

COPY --from=build-env /App/out .

EXPOSE 8080

ENTRYPOINT [ "dotnet" , "docker-dotnet-core-webapi.dll" ]



# FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build-env
# WORKDIR /app
# COPY ["docker-dotnet-core-webapi/docker-dotnet-core-webapi.csproj","docker-dotnet-core-webapi"]
# RUN dotnet restore "docker-dotnet-core-webapi.csproj"
# COPY . .
# WORKDIR "/app/docker-dotnet-core-webapi"
# RUN dotnet build "docker-dotnet-core-webapi.csproj" -c Release -o /app/build

# FROM build AS publish
# RUN dotnet publish "docker-dotnet-core-webapi.csproj" -c Release -o /app/publish

# FROM base AS final
# WORKDIR /app
# COPY --from=publish /app/publish .
# EXPOSE 8085
# ENTRYPOINT [ "dotnet" , "docker-dotnet-core-webapi.dll" ]