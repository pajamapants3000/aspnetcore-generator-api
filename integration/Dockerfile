FROM mcr.microsoft.com/dotnet/core/sdk:3.1
WORKDIR /integration

COPY integration.csproj .
RUN dotnet restore

COPY . .
ENV TEAMCITY_PROJECT_NAME=fake
ENTRYPOINT ["dotnet", "test", "integration.csproj", "--logger:\"console;verbosity=normal\""]

