GO := go
BUILDTAGS := "exclude_graphdriver_btrfs containers_image_openpgp remote"
BIN = ./bin

.PHONY: build
build:
	CGO_ENABLED=0 $(GO) build $(BUILDFLAGS) -o $(BIN)/ai-services -tags $(BUILDTAGS) ./cmd/ai-services
