install-promtail:
	helm upgrade --install promtail promtail \
		--repo https://grafana.github.io/helm-charts \
		--namespace promtail \
		--create-namespace \
		--values promtail.values.yml
