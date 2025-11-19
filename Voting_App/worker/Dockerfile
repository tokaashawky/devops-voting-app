FROM mcr.microsoft.com/dotnet/runtime:7.0 AS base
WORKDIR /app

FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /src
COPY . .
RUN dotnet restore

RUN dotnet publish -c Release -o /app/publish


FROM base AS final
WORKDIR /app
RUN useradd -m toka
COPY --from=build /app/publish .
RUN chown -R toka:toka /app
USER toka

ENTRYPOINT ["dotnet", "Worker.dll"]
