# Use an official Centos as parent image
FROM centos:7.4.1708

MAINTAINER Stas Goshtein <stas@perimeterx.com>

ENV container docker

# Enable EPEL repository and install packages
RUN yum install epel-release -y && \
    yum update -y && \
    yum install install mc nc vim-common wget sysstat htop figlet initscripts -y && \
    yum clean all

# Copy SELinux configuration
COPY selinux-config /etc/selinux/config

# Workaround for systemd
RUN (cd /lib/systemd/system/sysinit.target.wants/; for i in *; do [ $i == systemd-tmpfiles-setup.service ] || rm -f $i; done); \
    rm -f /lib/systemd/system/multi-user.target.wants/*;\
    rm -f /etc/systemd/system/*.wants/*;\
    rm -f /lib/systemd/system/local-fs.target.wants/*; \
    rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
    rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
    rm -f /lib/systemd/system/basic.target.wants/*;\
    rm -f /lib/systemd/system/anaconda.target.wants/*;

# Add figlet to MOTD
RUN figlet "CentOS7 Docker" > /etc/motd

VOLUME ["/sys/fs/cgroup"]

VOLUME /run /run/lock /tmp

CMD ["/usr/sbin/init"]