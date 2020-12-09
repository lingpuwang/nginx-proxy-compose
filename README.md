# nginx-proxy-compose

## How to use

- Start proxy server

```bash
docker-compose up -d
```

- Stop proxy server

```bash
docker-compose down
```

- Start proxied containers

Define a external network on the container to connect to the network of nginx-proxy.

```yml
services:
  web:
    ...
    environment:
      VIRTUAL_HOST: subdomain.yourdomain.tld
      LETSENCRYPT_HOST: subdomain.yourdomain.tld
    networks:
      - default
      - proxy

networks:
  proxy:
    external:
      name: nginx-proxy-compose_default
```
