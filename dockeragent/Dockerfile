# Use Maven with OpenJDK 17 as the base image
FROM maven:3.8.5-openjdk-17

# Set environment variables for Docker installation
ENV DOCKER_VERSION=20.10.24

# Install necessary packages for Docker installation
RUN apt-get update && \
    apt-get install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release && \
    curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add - && \
    echo "deb [arch=$(dpkg --print-architecture)] https://download.docker.com/linux/debian $(lsb_release -cs) stable" > /etc/apt/sources.list.d/docker.list && \
    apt-get update && \
    apt-get install -y docker-ce=${DOCKER_VERSION}~3-0~debian

# Clean up APT when done
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Verify Docker installation
RUN docker --version

# Set the working directory
WORKDIR /app

# Default command to run
CMD ["bash"]
