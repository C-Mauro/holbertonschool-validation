BINARY_NAME := awesome-api
LOG_FILE := awesome-api.log

.PHONY: all
all: build

.PHONY: build
build:
	go build -o $(BINARY_NAME)

.PHONY: run
run:
	nohup ./$(BINARY_NAME) > $(LOG_FILE) 2>&1 &

.PHONY: stop
stop:
	-kill "$(shell pgrep $(BINARY_NAME))"

.PHONY: clean
clean: stop
	-rm -f $(BINARY_NAME) $(LOG_FILE)

.PHONY: test
test:
	@echo "Testing with curl..."
	@curl -sS http://localhost:9999 || true
	@curl -sS http://localhost:9999/health || true
	@echo

.PHONY: help
help:
	@echo "Available targets:"
	@echo "  build     - Compile the source code to a binary"
	@echo "  run       - Run the application in the background"
	@echo "  stop      - Stop the running application"
	@echo "  clean     - Stop the application and remove the binary and log file"
	@echo "  test      - Perform test requests using curl"
	@echo "  help      - Display this help message"

