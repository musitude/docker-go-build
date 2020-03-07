build:
	docker build -t musitude/go-build:latest .
	docker tag musitude/go-build:latest musitude/go-build:$(shell git rev-parse HEAD)

push:
	docker login -u musitude
	docker push musitude/go-build:latest
	docker push musitude/go-build:$(shell git rev-parse HEAD)
