# Standalone Binary

{% hint style="warning" %}
### Unorthodox network is not live yet

These instructions may update at any time.
{% endhint %}

## Pre-requisites

This guide assumes use of Debian-based operating systems. Additional support for other operating systems and architecture will be added.

* 2 core CPU at a minimum(recommended 4-8 cores).
* 4 GB of RAM minimum (recommended 8GB).
* 50 GB of storage (recommended 100GB to be future-proof).
* glibc 2.29 library installed (required to run binary).
* chrony or ntp service running (required for time synchronisation).

## One-line startup Script

This script performs all the installation and configuration steps as outlined below in the article.

```bash
# replace <data-dir> with your specific directory, e.g. /data
# replace <name> with your node name, e.g. Test Validator
curl -fsSL https://raw.githubusercontent.com/digitalnativeinc/standard-substrate/master/scripts/opportunity-oneline.sh | bash -s <data-dir> <name>
```

## Build

### Using pre-built binary

We build and package binaries using Github Actions - [Github Actions build](https://github.com/digitalnativeinc/standard-substrate/actions/workflows/binary-build.yml). Compiled binaries are available from [Github Releases](https://github.com/digitalnativeinc/standard-substrate/releases) page.

{% hint style="danger" %}
Amend `<version>` in the script below to the latest latest in the Github Repository, e.g. 0.9.12.
{% endhint %}

{% tabs %}
{% tab title="linux/amd64" %}
```
# pulls latest release tag and sets it as var
LATEST_RELEASE=`curl --silent "https://api.github.com/repos/digitalnativeinc/standard-substrate/releases/latest" | grep '"tag_name":' | sed -E 's/.*"([^"]+)".*/\1/'`

# downloads binary based on latest tag set
wget -O opportunity-standalone https://github.com/digitalnativeinc/standard-substrate/releases/download/$LATEST_RELEASE/opportunity-standalone-linux-x86_64
```
{% endtab %}

{% tab title="darwin/amd64" %}
```
# pulls latest release tag and sets it as var
LATEST_RELEASE=`curl --silent "https://api.github.com/repos/digitalnativeinc/standard-substrate/releases/latest" | grep '"tag_name":' | sed -E 's/.*"([^"]+)".*/\1/'`

# downloads binary based on latest tag set
wget -o opportunity-standalone https://github.com/digitalnativeinc/standard-substrate/releases/download/$LATEST_VERSION/opportunity-standalone-darwin-x86_64
```
{% endtab %}
{% endtabs %}

### Building from source

#### Clone repository and navigate to it

```bash
git clone --recursive https://github.com/digitalnativeinc/standard-substrate.git && cd standard-substrate
```

#### Install Rust

Up-to-date instructions on how to install Rust are available here: [https://substrate.dev/docs/en/knowledgebase/getting-started/](https://substrate.dev/docs/en/knowledgebase/getting-started/)

```bash
curl https://sh.rustup.rs -sSf | sh -s -- -y && source $HOME/.cargo/env
```

{% hint style="info" %}
Do not install Rust toolchain, since we need a specific nightly build, referenced in the next step.
{% endhint %}

#### Install Rust project dependencies

{% tabs %}
{% tab title="Commands" %}
```
rustup default stable
rustup update stable
rustup install nightly-2021-11-07
rustup target add wasm32-unknown-unknown --toolchain nightly-2021-11-07
```
{% endtab %}

{% tab title="Makefile" %}
```
make init
```
{% endtab %}
{% endtabs %}

#### Run build

Depending on machine specifications, this build will run for between 30 and 90 minutes.

{% tabs %}
{% tab title="Command" %}
```
cargo build --release --bin standard-collator
```
{% endtab %}

{% tab title="Makefile" %}
```
make build
```
{% endtab %}
{% endtabs %}

## Run

The following script will do the following:

* Make it executable
* Setup systemd unit to run it as a service
* Enable it to run it on boot
* Check the status of the service

You can run these commands using a script, or separately copying commands.

{% hint style="info" %}
You can see all available flags by running command`./standard-opportunity --help`
{% endhint %}

{% hint style="warning" %}
Following commands assume running them with sudo.

_Additional options for running with a separate user will be added later._

_You will need to adjust several settings from the snippet below, e.g. \<data-dir>/\<node-name>._
{% endhint %}

{% tabs %}
{% tab title="Ubuntu Linux" %}
```
# ensure binary is executable
chmod +x ./standard-collator

# move binary to the bin folder
mv standard-collator /usr/local/bin

# create systemd unit file
touch /etc/systemd/system/standard-collator.service

# paste content into the file
# copy everything line 12-28 inclusive
cat > /etc/systemd/system/standard-collator.service << EOF
[Unit]
Description=Standard Collator

[Service]
ExecStart=/usr/local/bin/standard-collator \
--base-path <data-dir> \
--chain opportunity \
--port 30333 \
--name <node-name> \
--validator
Restart=always
RestartSec=120

[Install]
WantedBy=multi-user.target
EOF

# reload systemd service to accept new unit
systemctl daemon-reload

# enable validator service to run on boot
systemctl enable standard-collator

# start the service
systemctl start standard-collator

# check status of the service
systemctl status standard-collator
```
{% endtab %}
{% endtabs %}

### Finishing notes

If all went well, your node will now show up on [Testnet Telemetry](https://telemetry.polkadot.io/#/Opportunity%20Standalone%20Testnet).

Please see section **Testnet Staking Guide** and specifically [Becoming a Validator](../testnet-staking-guide/bonding-opt-token/becoming-a-validator.md) for further steps.
