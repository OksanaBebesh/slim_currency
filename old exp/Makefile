init: docker-down-clear docker-down docker-pull docker-build docker-up
docker-up:
	docker-compose up -d

docker-down:
	docker-compose down

docker-build:
	docker-compose build

docker-pull:
	docker-compose pull

docker-down-clear:
	docker-compose down -v --remove-orphans