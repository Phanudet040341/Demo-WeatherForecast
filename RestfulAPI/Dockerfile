FROM mcr.microsoft.com/dotnet/sdk:5.0
RUN apt-get update && apt-get install -y procps \
 && apt-get install -y tzdata
RUN apt-get install -y net-tools && apt-get install -y telnet
RUN ln -fs /usr/share/zoneinfo/Asia/Bangkok /etc/localtime
RUN dpkg-reconfigure --frontend noninteractive tzdata
WORKDIR /usr/src/bin
COPY . ./


ENTRYPOINT ["dotnet", "Magellan.Core.Provisioning.Things.APIs.dll"]