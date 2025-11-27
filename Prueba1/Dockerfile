FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS base
WORKDIR /app
EXPOSE 10000

FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src
COPY ["Prueba1.csproj", "./"]
RUN dotnet restore "Prueba1.csproj"
COPY . .
RUN dotnet build "Prueba1.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "Prueba1.csproj" -c Release -o /app/publish
 
FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "Prueba1.dll"] 