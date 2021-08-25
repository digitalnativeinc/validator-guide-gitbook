---
description: Page details upgrade instructions for nodes.
---

# Upgrade

## Binary

In order to upgrade automatically you can run the following oneline script:

{% hint style="info" %}
This assumes running Ubuntu paired with systemd.

Other implementation will be added later on.
{% endhint %}

```text
curl -fsSL https://raw.githubusercontent.com/digitalnativeinc/standard-substrate/master/scripts/oneline-upgrade.sh | bash
```

### Commands:

    # set env var for file
    export FILE="/usr/local/bin/opportunity-standalone"

    # stops the process
    sudo systemctl stop standard-validator

    # moves binary to be a backup
    mv $FILE $FILE-backup

    # pulls latest release tag and sets it as var
    export LATEST_RELEASE=`curl --silent "https://api.github.com/repos/digitalnativeinc/standard-substrate/releases/latest" | grep '"tag_name":' | sed -E 's/.*"([^"]+)".*/\1/'`

    # downloads binary based on latest tag set
    wget -O $FILE https://github.com/digitalnativeinc/standard-substrate/releases/download/$LATEST_RELEASE/opportunity-standalone-linux-x86_64

    # make binary executable
    chmod +x $FILE

    # restart the service
    systemctl start standard-validator

    # check it started up correctly
    systemctl status standard-validator --no-pager -o cat

    # check logs to see if there are any issues
    journalctl -u standard-validator -f

## Docker

{% hint style="danger" %}
Under construction
{% endhint %}

