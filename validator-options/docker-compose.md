---
description: Instruction on how to run Standard Validator with Docker Compose.
---

# Docker Compose

Published Docker images are available from the [standardtech](https://hub.docker.com/u/standardprotocol) organization repository.

Docker installation instructions are available [here](https://docs.docker.com/engine/install/).

Github Actions pipeline for Docker images can be found [here](https://github.com/digitalnativeinc/standard-substrate/actions/workflows/docker-build.yml).

## Run

### Use published image

Docker compose script is available in Standard Substrate repository [here](https://raw.githubusercontent.com/digitalnativeinc/standard-substrate/master/Docker/docker-compose.yml).

#### Run docker-compose script

{% tabs %}
{% tab title="Commands" %}
```text
# replace #NAME with custom name of your validator
NAME=#NAME docker-compose -f standard-substrate/Docker/docker-compose.yml up --detached
```
{% endtab %}

{% tab title="Makefile" %}
```
NAME='validator' make docker-compose-run
```
{% endtab %}
{% endtabs %}

### Build image

#### Run docker-compose script

{% tabs %}
{% tab title="Commands" %}
```text
# replace #NAME with custom name of your validator
NAME=#NAME docker-compose -f standard-substrate/Docker/docker-compose.yml up --detached
```
{% endtab %}

{% tab title="Makefile" %}
```
NAME='validator' make docker-compose-build-run
```
{% endtab %}
{% endtabs %}

