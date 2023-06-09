install-ingress-nginx:
	helm upgrade --install \
		ingress-nginx ingress-nginx \
		--repo https://kubernetes.github.io/ingress-nginx \
		--create-namespace \
		--namespace ingress-nginx \
		--set controller.service.type=ClusterIP \
		--set controller.ingressClassResource.default=true \
		--set controller.kind=DaemonSet \
		--set controller.hostPort.enabled=true \
		--set controller.metrics.enabled=true \
		--set controller.config.use-proxy-protocol=false \
		--wait

install-cert-manager:
	helm upgrade --install \
		cert-manager cert-manager \
		--repo https://charts.jetstack.io \
		--create-namespace \
		--namespace cert-manager \
		--set installCRDs=true \
		--wait

install-cluster-issuer:
	kubectl apply -f clusterissuer.yml

install-hello-world:
	helm upgrade --install \
		hello-world hello-world \
		--repo https://helm.sikalabs.io \
		--create-namespace \
		--namespace hello-world \
		--set host=hello.sikademo3.uk \
		--set replicas=2 \
		--set TEXT="Hello Microcomp" \
		--wait

install-argocd:
	helm upgrade --install \
		argocd argo-cd \
		--repo https://argoproj.github.io/argo-helm \
		--create-namespace \
		--namespace argocd \
		--set 'server.ingress.enabled=true' \
		--set 'server.ingress.hosts[0]='argocd.sikademo3.uk \
		--set 'server.ingress.ingressClassName=nginx' \
		--set 'server.ingress.annotations.cert-manager\.io/cluster-issuer=letsencrypt' \
		--set 'server.ingress.annotations.nginx\.ingress\.kubernetes\.io/server-snippet=proxy_ssl_verify off;' \
		--set 'server.ingress.annotations.nginx\.ingress\.kubernetes\.io/backend-protocol=HTTPS' \
		--set 'server.ingress.tls[0].hosts[0]=argocd.sikademo3.uk' \
		--set 'server.ingress.tls[0].secretName=argocd-tls' \
		--wait

get-argocd-password:
	@slu argocd initial-password
