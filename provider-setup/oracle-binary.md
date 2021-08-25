# Oracle Binary

## Pre-requisites

This guide assumes use of Debian-based operating systems. Additional support for other operating systems and architecture will be added.

* 2 core CPU at a minimum\(recommended 4-8 cores\).
* 4 GB of RAM minimum \(recommended 8GB\).
* Node.js v14 or higher installed \(required to run binary\).
* Configuration json file

### Configuration File

Configuration file now consists of four properties:

```text
{
   "nomics": "<nomics API Access Key>", // for crypto data fetch
   "finnhub": "<finnhub API Access Key>", // for fiat data fetch
   "mnemonic": "<mnemonic of oracle stash account>", // for data submission
   "rpc": "<rpc endpoint of the network>" // network to submit
 }
```

Make configuration file and save the sensitive data in a safe directory. 

## One-line startup Script

This script performs all the installation and configuration steps as outlined below in the article.

```bash
# replace <settings-dir> with your directory of specific settings file directory, e.g. /lumen-settings/settings.json
# settings.json should be like:
# {
#    "<data source>": "<Data source Access Key>",
#    ...
#    "mnemonic": "<mnemonic of oracle stash account>0",
#    "rpc": "<rpc endpoint of the network"
# }
npm i -g @digitalnative/lumen | lumen <settings-dir>
```

## Build

### Github

We build and maintain binaries using [Github](https://github.com/digitalnativeinc/lumen). Compiled binaries are available from [NPM Versions](https://www.npmjs.com/package/@digitalnative/lumen?activeTab=versions) page.

### Building from sources

After cloning from Github, developers can build the binary in local environment. The computer should install:

* lerna
* yarn

After installing these software, go to the root directory of the repository then run command

```text
yarn    
```

Then, the packages will be bootstrapped. After that, go to `core` package repo and then execute javascript code with the following command:

```text
node dist/index.js run <directory to lumen config json file>
```

