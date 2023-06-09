cert_sikademo3.uk:
ifndef CLOUDFLARE_DNS_API_TOKEN
	$(error CLOUDFLARE_DNS_API_TOKEN is not set)
endif
	lego --email ondrejsika@ondrejsika.com --dns cloudflare \
		--domains sikademo3.uk \
		--domains '*.sikademo3.uk' \
		--domains '*.apps.sikademo3.uk' \
		run
