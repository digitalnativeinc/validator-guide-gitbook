---
description: Instructions on how to run Standard Validator using Docker image.
---

# Docker

Published Docker images are available from the [standardtech](https://hub.docker.com/u/standardprotocol) organization repository.

Docker installation instructions are available [here](https://docs.docker.com/engine/install/).

Github Actions pipeline for Docker images can be found [here](https://github.com/digitalnativeinc/standard-substrate/actions/workflows/docker-build.yml).

## Pull/Build

### Use published image

{% hint style="info" %}
You can either pull latest release in format of \*.\*.\* from Github Releases, or use 'latest' tag.
{% endhint %}

```text
# pulls down latest tag
docker pull standardprotocol/opportunity-standalone:latest

# pulls down custom tag
docker pull standardprotocol/opportunity-standalone:0.x.x
```

### Build image from source

#### Clone repository

```bash
git clone https://github.com/digitalnativeinc/standard-substrate.git
```

#### Navigate to the cloned directory

```bash
cd standard-substrate
```

#### Build

{% tabs %}
{% tab title="Command" %}
```text
DOCKER_BUILDKIT=1 docker build -f Docker/Dockerfile -t opportunity-standalone:local .
```
{% endtab %}

{% tab title="Makefile" %}
```
make docker-build
```
{% endtab %}
{% endtabs %}

## Run

### Prepare

```bash
# will output --help command for opportunity-standalone
docker run standardprotocol/opportunity-standalone:latest
OR
docker run opportunity-standalone:local

# create separate volume for docker for persistence
docker volume create standard-validator-volume
```

### Run published image

{% tabs %}
{% tab title="Bash" %}
```bash
# start node
docker run -itd \
--volume standard-validator-volume:/data \
--name standard-validator \
standardprotocol/opportunity-standalone \
--base-path /data --name <node-name>
```
{% endtab %}

{% tab title="Makefile" %}
```

```
{% endtab %}
{% endtabs %}

### Run local image

{% tabs %}
{% tab title="Bash" %}
```bash
# start node
docker run -itd \
--volume standard-validator-volume:/data \
--name standard-validator \
opportunity-standalone:local \
--base-path /data --name <node-name>
```
{% endtab %}

{% tab title="Makefile" %}
```
# arguments given as a reference
make docker-run VOLUME_PATH='./data' DATA_DIR='/data' NODE_NAME='Standard Validator'
```
{% endtab %}
{% endtabs %}

### Check logs

```bash
docker logs standard-validator -f
```

