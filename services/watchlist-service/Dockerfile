FROM mcr.microsoft.com/dotnet/sdk:8.0 AS builder
WORKDIR /src

COPY WatchlistService.csproj .
RUN dotnet restore

COPY . .
RUN dotnet publish -c Release -o /app/publish --no-restore

FROM mcr.microsoft.com/dotnet/aspnet:8.0-alpine
WORKDIR /app

COPY --from=builder /app/publish .

USER app
EXPOSE 8080
CMD ["dotnet", "WatchlistService.dll"]