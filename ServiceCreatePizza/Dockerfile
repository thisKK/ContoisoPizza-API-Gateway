# Stage 1
FROM mcr.microsoft.com/dotnet/sdk:5.0 as build
WORKDIR /APP
COPY /ServiceCreatePizza /ServiceCreatePizza
RUN dotnet build /ServiceCreatePizza

# Stage 2
FROM build as publish
WORKDIR /APP
RUN dotnet publish /ServiceCreatePizza -c Release -o /APP -r linux-x64

# Stage 3
FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS runtime
WORKDIR /APP
COPY --from=publish /APP .
CMD dotnet ServiceCreatePizza.dll
