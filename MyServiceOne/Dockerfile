ARG ARCH=amd64
ARG TAG=6.0-bullseye-slim-$ARCH
FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /source

# copy csproj and restore as distinct layers
#COPY *.sln .
COPY ./MyServiceOne.csproj .
RUN dotnet restore

# copy everything else and build app
COPY . .
WORKDIR /source/
RUN dotnet publish -c release -o /app --no-restore

# final stage/image
FROM mcr.microsoft.com/dotnet/aspnet:$TAG
WORKDIR /app
COPY --from=build /app ./
ENTRYPOINT ["dotnet", "MyServiceOne.dll"]