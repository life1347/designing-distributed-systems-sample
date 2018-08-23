# SSL Termination Proxy

## Generate SSL crt

```bash
$ openssl dhparam -out dhparam.pem 512
$ openssl req -x509 -nodes -days 365 -newkey rsa:512 -keyout nginx.key -out nginx.crt
```
## Create Kubernetes Secret

```bash
$ kubectl create secret generic ssl-crt --from-file=dhparam.pem --from-file=nginx.crt--from-file=nginx.key
```

## Deploy

```bash
$ kubectl apply -f deploy.yaml
```