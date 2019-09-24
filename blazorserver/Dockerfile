FROM mcr.microsoft.com/dotnet/core/sdk:3.0

WORKDIR /app

COPY . .

RUN dotnet restore

RUN dotnet build

RUN dotnet publish -o /publish

ENTRYPOINT ["dotnet", "/publish/app.dll"]