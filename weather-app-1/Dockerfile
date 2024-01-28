#See https://aka.ms/customizecontainer to learn how to customize your debug container and how Visual Studio uses this Dockerfile to build your images for faster debugging.

#FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
#WORKDIR /app
#EXPOSE 80
#
#FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
#WORKDIR /src
#COPY ["weather-app-1/weather-app-1.csproj", "weather-app-1/"]
#RUN dotnet restore "weather-app-1/weather-app-1.csproj"
#COPY . .
#WORKDIR "/src/weather-app-1"
#RUN dotnet build "weather-app-1.csproj" -c Release -o /app/build
#
#FROM build AS publish
#RUN dotnet publish "weather-app-1.csproj" -c Release -o /app/publish /p:UseAppHost=false
#
#FROM base AS final
#WORKDIR /app
#COPY --from=publish /app/publish .
#ENTRYPOINT ["dotnet", "weather-app-1.dll"]

FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app
EXPOSE 80

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
COPY ["weather-app-1.csproj", "./"]
RUN dotnet restore "./weather-app-1.csproj"
COPY . .
WORKDIR "/src/."
RUN dotnet build "weather-app-1.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "weather-app-1.csproj" -c Release -o /app/publish /p:UseAppHost=false

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "weather-app-1.dll"]