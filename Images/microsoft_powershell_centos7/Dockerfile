# Docker image file that describes an Centos7 image with PowerShell installed from Microsoft YUM Repo

FROM centos:7
MAINTAINER Raghu Shantha <raghus@microsoft.com>

# Setup the locale
ENV LANG en_US.UTF-8
ENV LC_ALL $LANG
RUN localedef --charmap=UTF-8 --inputfile=en_US $LANG

# Install dependencies and clean up
RUN yum install -y \
        glibc \
        libcurl \
        ca-certificates \
        libgcc \
        libicu \
        openssl \
        libstdc++ \
        ncurses-base \
        libunwind \
        uuid \
        zlib \
        which \
        curl \
        git \
    && yum clean all

# Download and configure Microsoft Repository config file
RUN curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/microsoft.repo

# Install latest powershell from Microsoft YUM Repo
RUN yum install -y \
        powershell

COPY PowerShellPackage.ps1 /

# Use PowerShell as the default shell
ENTRYPOINT [ "powershell" ]
