FROM mcr.microsoft.com/dotnet/sdk:8.0 AS builder
WORKDIR /app
COPY src/*.csproj ./
RUN dotnet restore
COPY src/ .
RUN dotnet publish -c Release -o /out

FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app
COPY --from=builder /out .
EXPOSE 7070
ENTRYPOINT ["dotnet", "cartservice.dll"]
