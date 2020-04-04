# Stage 0 - Build Stage - build-env
FROM mcr.microsoft.com/dotnet/core/sdk:3.1 as build-env
WORKDIR /api

COPY api.csproj .
RUN dotnet restore

COPY . .
# publish for testing/debugging
#RUN dotnet publish -o /publish
# publish for prod
RUN dotnet publish -c Release -o /publish

# Stage 1 - Runtime Image Stage
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
ENV ASPNETCORE_ENVIRONMENT="Development"
ENV ASPNETCORE_URLS="http://0.0.0.0:80"
WORKDIR /publish
COPY --from=build-env /publish .
ENTRYPOINT ["dotnet", "api.dll"]
