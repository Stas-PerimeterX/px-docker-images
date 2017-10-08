# Use Centos7 common as a base image
FROM px-centos7-common:latest

# Install Redis
RUN yum install redis -y && yum clean all

USER root

# Mountable directories
VOLUME ["/data"]

# Set the environment variables
ENV HOME /var/lib/redis

# Working directory
WORKDIR /var/lib/redis

# Copy master configuration file
COPY redis-slave.conf /etc/redis.conf

# Start Redis Server
CMD ["/usr/bin/redis-server", "/etc/redis.conf"]

# Check Slave
#RUN redis-cli -p 6379 ping

# Expose port 6379
EXPOSE 6379
