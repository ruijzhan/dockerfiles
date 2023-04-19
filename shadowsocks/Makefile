# Specify that these targets do not represent files
.PHONY: all docker-build docker-push clean

# Set CPU_ARCH variable based on system architecture
CPU_ARCH := $(shell uname -m | sed -e 's/x86_64/amd64/' -e 's/aarch64/arm64/')

# Set version numbers for various components used in Docker image
KCP_VERSION := 20230214
SS_LIBEV_VERSION := v3.3.5
V2RAY_PLUGIN_VERSION := v1.3.2

# Set Docker image name and tag based on architecture
IMAGE_NAME := ruijzhan/shadowsocks
IMAGE_TAG := $(CPU_ARCH)

# Define target to build Docker image with specified arguments
docker-build:
	docker build \
	--build-arg SS_LIBEV_VERSION=$(SS_LIBEV_VERSION) \
	--build-arg V2RAY_PLUGIN_VERSION=$(V2RAY_PLUGIN_VERSION) \
	--build-arg ARCH=$(CPU_ARCH) \
	--build-arg KCP_VERSION=$(KCP_VERSION) \
	-t $(IMAGE_NAME):$(IMAGE_TAG) .

# Define target to push Docker image to registry
docker-push:
	docker push $(IMAGE_NAME):$(IMAGE_TAG)

# Define target to remove Docker image from local machine
clean:
	docker rmi $(IMAGE_NAME):$(IMAGE_TAG)
