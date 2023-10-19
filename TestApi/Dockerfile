#See https://aka.ms/customizecontainer to learn how to customize your debug container and how Visual Studio uses this Dockerfile to build your images for faster debugging.

#FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS base
#WORKDIR /app
#
#
#FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
#WORKDIR /src
#COPY *.csproj .
#RUN dotnet restore "TestApi/TestApi.csproj"
#COPY . .
#WORKDIR "/src/TestApi"
#RUN dotnet build "TestApi.csproj" -c Release -o /app/build
#
#FROM build AS publish
#RUN dotnet publish "TestApi.csproj" -c Release -o /app/publish /p:UseAppHost=false
#
#FROM base AS final
#WORKDIR /app
#COPY --from=publish /app/publish .
#ENTRYPOINT ["dotnet", "TestApi.dll"]

#
FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS base
WORKDIR /app


COPY *.csproj .

RUN dotnet restore

COPY . ./

RUN dotnet publish --no-restore -c Release -o out

FROM mcr.microsoft.com/dotnet/core/aspnet:5.0
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet", "Api.dll"]