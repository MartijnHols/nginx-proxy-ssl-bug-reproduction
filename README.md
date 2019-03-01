# jwilder/nginx-proxy SSL fallback issue reproduction

This is a minimal reproduction of the jwilder/nginx-proxy bug where SSL connections return a (random) different server when a container listening to the VIRTUAL_HOST being requested (temporarily) goes down. To reproduce:

1. `docker-compose up -d`
2. Go to: https://s1.localhost
3. Continue anyway when it warns about the certificate, the SSL certificate is not supported to be valid. That's not the point.
4. Take note of the "server name"
5. `docker-compose stop s1`
6. Refresh the page, note that the "server name" changed to s2
