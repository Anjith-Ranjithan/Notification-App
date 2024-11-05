# Use the .NET SDK image to build the app
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src
COPY ["NotificationApi.csproj", "./"]
RUN dotnet restore "./NotificationApi.csproj"
COPY . .
RUN dotnet publish "NotificationApi.csproj" -c Release -o /app/publish

# Use the ASP.NET Core runtime image to run the app
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS base
WORKDIR /app
EXPOSE 80
COPY --from=build /app/publish .
ENTRYPOINT ["dotnet", "NotificationApi.dll"]
