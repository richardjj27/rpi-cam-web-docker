default:
	@echo pass
dev-build:
	docker build -t richardjj627/rpi-cam-web:develop-setup .
	docker run -it --name=rpi-cam-web-setup -p=80:80/tcp --volume=/opt/vc:/opt/vc --device=/dev/vchiq --device=/dev/vcsm richardjj627/rpi-cam-web:develop-setup
	docker commit rpi-cam-web-setup richardjj627/rpi-cam-web:develop-preinstall
	+$(MAKE) .rm-run
	docker rmi richardjj627/rpi-cam-web:develop-setup
latest-build:
	docker build -t richardjj627/rpi-cam-web:release-setup -f Dockerfile.latest .
	docker run -it --name=rpi-cam-web-setup -p=80:80/tcp --volume=/opt/vc:/opt/vc --device=/dev/vchiq --device=/dev/vcsm richardjj627/rpi-cam-web:release-setup
	docker commit rpi-cam-web-setup richardjj627/rpi-cam-web:release-preinstall
	+$(MAKE) .rm-run
	docker rmi richardjj627/rpi-cam-web:release-setup
.rm-run:
	docker rm rpi-cam-web-setup
release: Dockerfile.latest
Dockerfile.latest:
	@echo "overwriting Dockerfile.latest"
	cp Dockerfile.latest Dockerfile.latest.bkp
	cp Dockerfile Dockerfile.latest
