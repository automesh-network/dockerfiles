FROM mcr.microsoft.com/windows/servercore:ltsc2022

SHELL ["powershell", "-Command", "$ErrorActionPreference = 'Stop'; $ProgressPreference = 'Continue'; $verbosePreference='Continue';"]
RUN Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))

RUN choco install visualstudio2022buildtools -y --package-parameters '--quiet --wait --norestart --add Microsoft.Component.MSBuild --add Microsoft.VisualStudio.Component.Windows11SDK.22621 --add Microsoft.VisualStudio.Component.VC.Tools.x86.x64 --add Microsoft.VisualStudio.Component.VC.Tools.ARM64'
RUN choco install git -y

ARG VCPKG_BINARY_SOURCES=
ARG ACTIONS_CACHE_URL=
ARG ACTIONS_RUNTIME_TOKEN=
ARG VCPKG_ROOT="C:\\vcpkg"
ARG VCPKG_VERSION=2024.03.25
RUN git clone https://github.com/microsoft/vcpkg.git $env:VCPKG_ROOT
RUN git -C $env:VCPKG_ROOT checkout $env:VCPKG_VERSION
RUN & "$env:VCPKG_ROOT\bootstrap-vcpkg.bat -disableMetrics"
RUN [Environment]::SetEnvironmentVariable('VCPKG_ROOT', $env:VCPKG_ROOT, [EnvironmentVariableTarget]::Machine)
RUN [Environment]::SetEnvironmentVariable('PATH', $env:PATH + ';' + $env:VCPKG_ROOT, [EnvironmentVariableTarget]::Machine)
