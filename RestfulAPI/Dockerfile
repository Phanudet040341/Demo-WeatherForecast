FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.sln .
COPY RestfulAPI/*.csproj ./RestfulAPI/
RUN dotnet restore

# copy everything else and build app
COPY RestfulAPI/. ./RestfulAPI/
WORKDIR /app/RestfulAPI
RUN dotnet publish -c Release -o out

FROM  mcr.microsoft.com/dotnet/sdk:5.0 AS runtime
WORKDIR /app
COPY --from=build /app/RestfulAPI/out .
EXPOSE 80
CMD ["dotnet", "RestfulAPI.dll"]