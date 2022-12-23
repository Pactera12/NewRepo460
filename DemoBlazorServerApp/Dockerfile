FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app
EXPOSE 80

 

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /app
COPY ["DemoBlazorServerApp.csproj", "."]
RUN dotnet restore "DemoBlazorServerApp.csproj"
COPY . .
RUN ls
RUN dotnet build "DemoBlazorServerApp.csproj"

 

FROM build AS publish
RUN dotnet publish "DemoBlazorServerApp.csproj" -c Release -o /app/publish

 

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "DemoBlazorServerApp.dll"]
