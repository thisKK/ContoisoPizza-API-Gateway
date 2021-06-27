# Stage 1
FROM mcr.microsoft.com/dotnet/sdk:5.0 as build
WORKDIR /APP
COPY /Gateway /Gateway
RUN dotnet build /Gateway

# Stage 2
FROM build as publish
WORKDIR /APP
RUN dotnet publish /Gateway -c Release -o /APP -r linux-x64

# Stage 3
FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS runtime
WORKDIR /APP
COPY --from=publish /APP .
CMD dotnet Gateway.dll
