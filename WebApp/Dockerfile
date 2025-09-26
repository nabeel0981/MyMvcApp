<<<<<<< HEAD
# Stage 1: Build
FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /src
COPY . .
RUN dotnet restore WebApp.csproj
RUN dotnet publish WebApp.csproj -c Release -o /app/publish

# Stage 2: Runtime
FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS runtime
=======
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
# Use the official .NET 9.0 SDK image to build and publish the app
FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /src

# Copy csproj and restore dependencies
COPY WebApp.csproj .
RUN dotnet restore WebApp.csproj

# Copy everything else and build
COPY . .
RUN dotnet publish WebApp.csproj -c Release -o /app/publish

# Use ASP.NET Core 9.0 runtime image for running the app
FROM mcr.microsoft.com/dotnet/aspnet:9.0 AS final
WORKDIR /app
COPY --from=build /app/publish .
ENTRYPOINT ["dotnet", "WebApp.dll"]
# Use the official .NET SDK image to build and publish the app
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src

# Copy csproj and restore dependencies
COPY WebApp.csproj .
RUN dotnet restore WebApp.csproj

# Copy everything else and build
COPY . .
RUN dotnet publish WebApp.csproj -c Release -o /app/publish

# Use ASP.NET Core runtime image for running the app
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS final
>>>>>>> bf637df (Dockerfile added)
WORKDIR /app
COPY --from=build /app/publish .
ENTRYPOINT ["dotnet", "WebApp.dll"]
