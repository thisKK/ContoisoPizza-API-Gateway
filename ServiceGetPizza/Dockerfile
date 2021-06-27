# Stage 1
FROM mcr.microsoft.com/dotnet/sdk:5.0 as build
WORKDIR /APP
COPY /ServiceGetPizza /ServiceGetPizza
RUN dotnet build /ServiceGetPizza

# Stage 2
FROM build as publish
WORKDIR /APP
RUN dotnet publish /ServiceGetPizza -c Release -o /APP -r linux-x64

# Stage 3
FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS runtime
WORKDIR /APP
COPY --from=publish /APP .
CMD dotnet ServiceGetPizza.dll
