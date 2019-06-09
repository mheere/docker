 
 # Stage 1
 FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS builder
 LABEL author="Marcel Heeremans"
 WORKDIR /app

 # caches restore result by copying csproj file separately
 COPY *.csproj .
 RUN dotnet restore

 # copies the rest of your code
 COPY . .
 RUN dotnet publish --output /mybuilder/ --configuration Release

 # Stage 2
 FROM mcr.microsoft.com/dotnet/core/sdk:2.2
 WORKDIR /app
 COPY --from=builder /mybuilder .
 ENTRYPOINT ["dotnet", "mh.dll"]