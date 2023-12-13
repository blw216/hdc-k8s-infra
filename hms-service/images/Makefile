build:
	docker build -t hms-standalone .
	docker tag hms-standalone 127.0.0.1:32000/hms-standalone
	# microk8s may require you to update Docker config to allow pushing to insecure registry over HTTP
	# https://microk8s.io/docs/registry-built-in
	docker push 127.0.0.1:32000/hms-standalone
	# Add the metastore-site.xml as a ConfigMap in k8s
	microk8s kubectl create configmap metastore-cfg --dry-run=client --from-file=metastore-site.xml -o yaml | microk8s kubectl apply -f -