# deployment

Deployment configuration for all components

## Preparation

- Install Docker and Docker-Compose
- Configure Firewall to allow traffic on necessary ports
- Firebase Account and necessary files for the Cloud-Agent (see cloud-agent README)
- Clone this repository recursively `git clone --recursive https://git.snet.tu-berlin.de/blockchain/dims/deployment.git`

## How to deploy

```shell
# add firebase admin sdk json file to ca-config directory
cp firebase-admin-sdk.json ca-config/firebase-admin-sdk.json

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

### API or CloudAgent: `PoolLedgerTimeout`

This happens sometimes when the pool was not quite ready on startup, try restarting the service, e.g.:
```shell
sudo docker-compose restart api
```
or
```shell
sudo docker-compose restart cloudagent
```

