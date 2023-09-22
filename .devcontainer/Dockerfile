FROM mcr.microsoft.com/devcontainers/rust:1-1-bullseye
COPY ./JLink_Linux_V792f_x86_64.deb /tmp/JLink_Linux_V792f_x86_64.deb
COPY ./nrf-command-line-tools_10.23.0_amd64.deb /tmp/nrf-command-line-tools_10.23.0_amd64.deb

RUN apt-get -qq -y update
RUN apt-get -qq -y upgrade
RUN apt-get -qq -y install vim
RUN apt-get -qq -y install libudev-dev udev
RUN apt-get -qq -y install usbutils
RUN apt-get -qq -y install libusb-dev
RUN apt-get -qq -y install gdb-multiarch

RUN /lib/systemd/systemd-udevd --daemon && apt-get -qq -y install /tmp/JLink_Linux_V792f_x86_64.deb && apt-get -qq -y install /tmp/nrf-command-line-tools_10.23.0_amd64.deb


USER vscode
RUN rustup target add thumbv7em-none-eabihf
RUN cargo install probe-run
RUN cargo install probe-rs --features cli
RUN cargo install flip-link
