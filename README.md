# KashisAU Server
## A dockerised minimal version of Kashi's VPS, configured for Nginx
This is a simple VPS initialisation repo that will run an Dockerised Nginx instance exposing subdomains for *.kashis.com.au. There is minimal configuration required for spinning this up.

## Prerequistes
A *nix-based VM (or phyiscal server) with Docker installed. Running the startup script will initialise an Nginx server, provided the correct files are in place for TLS.

## Secrets
There are a few secrets required for the Nginx server to serve domains on *.kashis.com.au, mostly to do with SSL configuration. Hence a directory called `./keys` will need to be provided, with the following files:

```
.
+-- keys/
|   +-- server.key # Server's private key
|   +-- domain-bundle.crt # Bundled signed domain certificate
|   +-- ca-certificate.pem # CA's trusted certificate
|   +-- dhparam.pem # A pre-calculated DH sequence
```

## Running
The `docker-compose.yml` file should hold all the config details required for configuration. This can be edited, and the `nginx/sites-available/example.kashis.com.au` config file edited to our liking. Once configured, the following command will begin the server:

```
docker-compose up -d
```