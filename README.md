# deployment

Deployment configuration for all components

### Warning: This repository contains credentials such as ca-config/firebase-adminsdk.json for firebase and may contain other sensitive information. Scrub the history and remove those files as well as any other kind of sensitive data before publishing.

## Preparation

- Install Docker and Docker-Compose
- Configure Firewall to allow traffic on necessary ports
- Firebase Account and necessary files for the Cloud-Agent (see cloud-agent README)
- Clone this repository recursively `git clone --recursive https://git.snet.tu-berlin.de/blockchain/dims/deployment.git`

## How to deploy

```shell
# add firebase admin sdk json file to ca-config directory,
# if it is not already there or you are updating
cp firebase-adminsdk.json ca-config/firebase-adminsdk.json

# configure oidc-provider with environment variables or edit
vim oidc-config/config.json

# get your publicly reachable ip address
curl ident.me

# copy env-example and edit accordingly
# e.g. with vim or any other editor
cp env-example .env
vim .env

# build images
sudo docker-compose build

# deploy
sudo docker-compose up -d
```

## Troubleshooting

### `PoolLedgerTimeout` (or pool connection issues in general)

This happens sometimes when the pool was not quite ready on startup, try restarting the service, e.g.:
```shell
sudo docker-compose restart api
```
or
```shell
sudo docker-compose restart cloudagent
```

