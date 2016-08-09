FROM microsoft/dotnet:1.0.0-preview1

RUN apt-get update && apt-get install -y --force-yes postgresql-client

WORKDIR /app

ADD src/ /app/src/

RUN dotnet restore -v minimal src/ \
    && dotnet publish -c Release -o ./ src/Worker/ \
    && rm -rf src/ $HOME/.nuget/

CMD dotnet Worker.dll
