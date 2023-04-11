.PHONY: all docker-build docker-push arch clean

CPU_ARCH := $(shell uname -m | sed -e 's/x86_64/amd64/' -e 's/aarch64/arm64/')
KCP_VERSION := 20230214
IMAGE_NAME := ruijzhan/kcptun
IMAGE_TAG := $(CPU_ARCH)

all: docker-build docker-push

docker-build:
	docker build --build-arg ARCH=$(CPU_ARCH) --build-arg KCP_VERSION=$(KCP_VERSION) -t $(IMAGE_NAME):$(IMAGE_TAG) .

docker-push:
	docker push $(IMAGE_NAME):$(IMAGE_TAG)

arch:
	@echo "The CPU architecture on this system is: $(CPU_ARCH)"
	@echo "The kcptun version is: $(KCP_VERSION)"

clean:
	docker rmi $(IMAGE_NAME):$(IMAGE_TAG)
