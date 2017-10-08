# Use Centos7 common as a base image
FROM px-centos7-common:latest

# Install Redis
RUN yum install redis -y && yum clean all

USER root

# Mountable directories
VOLUME ["/data-master", "/data-slave"]

# Set the environment variables
ENV HOME /var/lib/redis

# Working directory
WORKDIR /var/lib/redis

# Copy master configuration file
COPY redis-master.conf /etc/redis-master.conf

# Copy slave configuration file
COPY redis-slave.conf /etc/redis-slave.conf

# Start Redis Master
#RUN ["/usr/bin/redis-server", "/etc/redis-master.conf"]

# Start Redis Slave
CMD ["/usr/bin/redis-server", "/etc/redis-slave.conf"]

# Check Master
#RUN redis-cli -p 6379 ping

# Check Slave
#RUN redis-cli -p 6380 ping

# Expose port 6379
EXPOSE 6379

# Expose port 6380
EXPOSE 6380
