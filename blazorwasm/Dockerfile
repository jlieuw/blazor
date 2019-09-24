FROM mcr.microsoft.com/dotnet/core/sdk:3.0-buster AS build

WORKDIR /src

COPY app.csproj .

RUN dotnet restore "app.csproj"
COPY . .
RUN dotnet build "app.csproj" -c Release -o /app/build
FROM build AS publish
RUN dotnet publish "app.csproj" -c Release -o /app/publish

FROM nginx:alpine AS final
WORKDIR /usr/share/nginx/html
COPY --from=publish /app/publish/app/dist .
COPY nginx.conf /etc/nginx/nginx.conf