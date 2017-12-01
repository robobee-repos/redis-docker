include ../utils/Makefile.help
include ../utils/Makefile.functions

export ROOT_DIR := $(shell realpath root)
export NAME := redis

.PHONY: test
test: setup ##@targets Starts docker compose.
	docker-compose -p $(NAME) -f test.yaml up

.PHONY: stop
stop: ##@targets Stops test containers.
	docker-compose -p $(NAME) -f test.yaml stop

.PHONY: rm
rm: stop ##@targets Removes test containers.
	docker-compose -p $(NAME) -f test.yaml rm

.PHONY: clean
clean: rm ##@targets Removes docker containers and created files.
	sudo rm -rf root

.PHONY: setup
setup:
	for p in data; do \
	mkdir -p root/$$p; \
	chmod o+rwX root/$$p ; \
	done
