# Stage 1: Build and publish the app
FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /src

# Copy csproj and restore dependencies
COPY WebApp.csproj .
RUN dotnet restore WebApp.csproj

# Copy everything else and build
COPY . .
RUN dotnet publish WebApp.csproj -c Release -o /app/publish

# Stage 2: Run the app with ASP.NET Core runtime
FROM mcr.microsoft.com/dotnet/aspnet:9.0 AS runtime
WORKDIR /app
COPY --from=build /app/publish .
ENTRYPOINT ["dotnet", "WebApp.dll"]
