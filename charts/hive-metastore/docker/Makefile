build:
	docker build -t hivemetastore .
	docker tag hivemetastore 127.0.0.1:32000/hivemetastore
	# Had to edit these two files:
	# sudo nano /var/snap/docker/current/etc/docker/daemon.json
	# sudo nano /var/snap/docker/current/config/daemon.json
	# And add "insecure-registries": ["127.0.0.1:32000"] to the json
	# So docker would communicate with the k8s private registry over HTTP
	# https://microk8s.io/docs/registry-private
	# Then `sudo snap stop docker && sudo snap disable docker`
	# Then `sudo snap enable docker && sudo snap start docker` 
	docker push 127.0.0.1:32000/hivemetastore