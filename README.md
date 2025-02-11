# Nick8Green Custom Actions

## Docker Deploy

Used to deploy docker containers to a VPS.

### Arguments

- **host** _`string`_ - The host of the VPS. Defaulted but can be passed in as a secret from another workflow. _(optional)_
- **image** _`string`_ - Image to deploy.
- **key** _`string`_ - The private key that can be used to authenticate to the VPS. Defaulted but can be passed in as a secret from another workflow. _(optional)_
- **name** _`string`_ - Name of the container.
- **network** _`string`_ - Network to connect the container to.
- **options** _`string`_ - Additional options to pass to the container on startup. _(optional)_
- **user** _`string`_ - The user to authenticate with the VPS. Defaulted but can be passed in as a secret from another workflow. _(optional)_
- **version** _`string`_ - Version to deploy. _(default: latest)_

### Usage

```
name: 

on:
  push:
    branches:
      - release

jobs:
  deploy:
    uses: nick8green/workflows/.github/workflows/deployment/docker-vps.yml@main
    with:
      image: alpine
      name: demo-container
      version: 3.21.2
    secrets:
      network: ${{ secrets.DOCKER_NETWORK }}
      options: "-v /tmp:/data"
```
