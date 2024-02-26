FROM ghcr.io/automesh-network/dockerfiles:rust-windows

RUN choco install openssl git strawberryperl just -y

ENV OPENSSL_DIR "C:\\Program Files\\OpenSSL-Win64"
ENV OPENSSL_LIB_DIR "C:\\Program Files\\OpenSSL-Win64\\lib\\VC\\x64\\MD"
RUN '[Environment]::SetEnvironmentVariable("Path", $env:Path + ";C:\Users\ContainerAdministrator\.cargo\bin", [EnvironmentVariableTarget]::Machine)'

RUN rustup.exe install 1.75 nightly-2023-12-30
RUN rustup.exe default 1.75

ADD https://raw.githubusercontent.com/cargo-bins/cargo-binstall/main/install-from-binstall-release.ps1 /install-from-binstall-release.ps1
RUN C:\install-from-binstall-release.ps1
RUN cargo binstall --secure --no-confirm cargo-tarpaulin cargo-audit cargo-nextest
