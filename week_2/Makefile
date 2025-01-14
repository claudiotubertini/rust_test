SHELL := /bin/bash

.PHONY: help clean build test lint format bump deploy

help: ## Show this help message
    @grep -E '^[a-zA-Z_-]+:.*?## .*$$' $(MAKEFILE_LIST) | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}'

clean: ## Clean the project
    cargo clean

build: ## Build the project
    cargo build

test: ## Run tests
    cargo test

lint: ## Run linter
    cargo clippy

format: ## Format the code
    @rustup component add rustfmt 2> /dev/null
    cargo fmt

bump: ## Bump the version number
    @echo "Current version is $(shell cargo pkgid | cut -d# -f2)"
    @read -p "Enter new version number: " version; \
    cargo set-version $$version

deploy: build ## Deploy the application
    @echo "Deploying the application..."
    # Add your deployment commands here, e.g., copying binaries to a server
    # scp target/release/your_app user@server:/path/to/deploy