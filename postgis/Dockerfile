FROM mcr.microsoft.com/windows/servercore:ltsc2022 as pgbase

# Install Chocolatey
RUN powershell -Command "Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))"

ARG PG_PASS

RUN choco install postgresql --params "/PASSWORD=%PG_PASS%" -y

RUN choco install postgis -y && \
    initdb -D "C:/Program Files/PostgreSQL/17/data" -U postgres && \ 
    net start postgresql-x64-17

