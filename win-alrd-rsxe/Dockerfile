FROM ghcr.io/automesh-network/dockerfiles:win-dev-rust

RUN vcpkg install openssl:x64-windows openssl:x64-windows-static openssl:x64-windows-static-md
RUN vcpkg install openssl:x86-windows openssl:x86-windows-static openssl:x86-windows-static-md
RUN vcpkg install openssl:arm64-windows openssl:arm64-windows-static openssl:arm64-windows-static-md

RUN choco install git strawberryperl just -y

ARG RUST_STABLE_VERSION=1.76
ARG RUST_NIGHTLY_VERSION=2024-02-08
RUN rustup install $env:RUST_STABLE_VERSION
RUN rustup default $env:RUST_STABLE_VERSION
RUN rustup install nightly-$env:RUST_NIGHTLY_VERSION

ADD https://raw.githubusercontent.com/cargo-bins/cargo-binstall/main/install-from-binstall-release.ps1 /install-from-binstall-release.ps1
RUN C:\install-from-binstall-release.ps1
RUN cargo binstall --secure --no-confirm cargo-tarpaulin cargo-audit cargo-nextest
