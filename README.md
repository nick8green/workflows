# Nick8Green Custom Actions

## Workflows

### Docker Deploy

Used to deploy docker containers to a VPS.

#### Arguments

- **host** _`string`_ - The host of the VPS. Defaulted but can be passed in as a secret from another workflow. _(optional)_
- **image** _`string`_ - Image to deploy.
- **key** _`string`_ - The private key that can be used to authenticate to the VPS. Defaulted but can be passed in as a secret from another workflow. _(optional)_
- **name** _`string`_ - Name of the container.
- **network** _`string`_ - Network to connect the container to.
- **options** _`string`_ - Additional options to pass to the container on startup. _(optional)_
- **token** _`string`_ - The user to GitHub authentication token in order to auth with the container registry. Defaulted but can be passed in as a secret from another workflow. _(optional)_
- **user** _`string`_ - The user to authenticate with the VPS. Defaulted but can be passed in as a secret from another workflow. _(optional)_
- **version** _`string`_ - Version to deploy. _(default: latest)_

#### Usage

```
[...]

jobs:
  deploy:
    uses: nick8green/workflows/.github/workflows/docker-deploy.yml@main
    with:
      image: alpine
      name: demo-container
      version: 3.21.2
    secrets:
      network: ${{ secrets.DOCKER_NETWORK }}
      options: "-v /tmp:/data"
```

### Node Build

TBC

#### Arguments

- **** _``_ - .

#### Usage

```
```

### Node Lint

TBC

#### Arguments

- **** _``_ - .

#### Usage

```
```

### Node Unit Tests

TBC

#### Arguments

- **** _``_ - .

#### Usage

```
```

## Composite Actions

### Node Setup

Initilises and then installs dependencies. If the dependencies are already cached then they are pulled from the cache rather than doing a fresh install.

#### Arguments

- **version** _`string`_ - The version of node to utilise.

#### Usage

```
[...]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Setup Node
        uses: nick8green/workflows/actions/node-setup.yml@main
        with:
          version: 22

[...]
```
