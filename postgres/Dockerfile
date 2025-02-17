FROM mcr.microsoft.com/windows/servercore:ltsc2022 as pgbase

ENV PG_INSTALL_PATH="C:/pgsql"
ENV PGDATA="C:/Program Files/PostgreSQL/17/"

# Install Chocolatey
RUN powershell -Command "Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))"

WORKDIR /Temp

RUN curl -L -o postgresql-installer.exe https://sbp.enterprisedb.com/getfile.jsp?fileid=1259363

WORKDIR %PGDATA%

RUN postgresql-installer.exe mode unattended ----datadir=%PGDATA%

WORKDIR C:/