## Action Coin

This is the official Action Coin repository.  This software is based on [Komodo Platform Technology](https://komodoplatform.com/).

## Resources

- Action Coin Website: [https://actioncoin.com](https://actioncoin.com/)
- Action Block Explorer: [https://exp.actioncoin.com](https://exp.actioncoin.com/)
- Support: [https://actioncoin.freshdesk.com/a/](https://actioncoin.freshdesk.com/a/)

## List of Platform Technologies

- Delayed Proof of Work (dPoW) - Additional security layer and Komodos own consensus algorithm. 
- zk-SNARKs - Komodo Platform's privacy technology for shielded transactions.  
- Tokens/Assets Technology - create "colored coins" on the Action Coin Blockchain and use them as a layer for rewards.

## Technical Specification

- Max Supply: 2 billion ACTN
- Block Time: 60 seconds
- 100% POS
- Equihash

## Block rewards over the next 10 years: 200,000,000 ACTN

- Year 1: 52,560,000 ACTN ~ Block Reward: 100 ACTN (525,600 blocks)
- Year 2: 52,560,000 ACTN ~ Block Reward: 100 ACTN (525,600 blocks)
- Year 3: 26,280,000 ACTN ~ Block Reward: 50 ACTN (525,600 blocks)
- Year 4: 26,280,000 ACTN ~ Block Reward: 50 ACTN (525,600 blocks)
- Year 5: 13,140,000 ACTN ~ Block Reward: 25 ACTN (525,600 blocks)
- Year 6: 13,140,000 ACTN ~ Block Reward: 25 ACTN (525,600 blocks)
- Year 7: 6,570,000 ACTN ~ Block Reward: 12.5 ACTN (525,600 blocks)
- Year 8: 6,570,000 ACTN ~ Block Reward: 12.5 ACTN (525,600 blocks)
- Year 9: 1,450,000 ACTN ~ Block Reward: 6.25 ACTN (525,600 blocks)
- Year 10: 1,450,000 ACTN ~ Block Reward: 6.25 ACTN (525,600 blocks)

## About this Project

Action Coin (“Action” or “ACTN”) is earned by joining our website, and participating in community activities (such as mining and staking).

Collectors may use their Action Coin to obtain deals and discounts (1.00 ACTN = $1.00 USD in SAVINGS) on a [growing list of products and services](https://actioncoin.com/rewards) offered by Vendors from more than 30 countries.

## Getting started

Detailed instructions coming soon.

### Dependencies

```shell
#Upgrade your system
sudo apt-get update
sudo apt-get upgrade -y
```

```shell
#The following packages are needed:
sudo apt-get install build-essential pkg-config libc6-dev m4 g++-multilib autoconf libtool ncurses-dev unzip git python python-zmq zlib1g-dev wget libcurl4-gnutls-dev bsdmainutils automake curl libsodium-dev
```

### Build

This software is based on zcash and considered experimental and is continously undergoing heavy development.

The dev branch is considered the bleeding edge codebase while the master-branch is considered tested (unit tests, runtime tests, functionality). At no point of time does Action Coin Inc., or the Komodo Platform developers take any responsbility for any damage out of the usage of this software. 
This software builds for all operating systems out of the same codebase. Follow the OS specific instructions from below.

#### Linux

```shell
git clone https://github.com/actioncoininc/action --branch master --single-branch
cd action
./zcutil/fetch-params.sh
./zcutil/build.sh -j$(expr $(nproc) - 1)
#This can take some time.
```

#### OSX

Ensure you have [brew](https://brew.sh) and Command Line Tools installed.
```shell
# Install brew
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
# Install Xcode, opens a pop-up window to install CLT without installing the entire Xcode package
xcode-select --install 
# Update brew and install dependencies
brew update
brew upgrade
brew tap discoteq/discoteq; brew install flock
brew install autoconf autogen automake
brew update && brew install gcc@8
brew install binutils
brew install protobuf
brew install coreutils
brew install wget
# Clone the Action Coin repo
git clone https://github.com/actioncoin/action --branch master --single-branch
# Change master branch to other branch you wish to compile
cd action
./zcutil/fetch-params.sh
./zcutil/build-mac.sh -j$(expr $(sysctl -n hw.ncpu) - 1)
# This can take some time.
```

#### Windows

Use a debian cross-compilation setup with mingw for windows and run:
```shell
sudo apt-get install build-essential pkg-config libc6-dev m4 g++-multilib autoconf libtool ncurses-dev unzip git python python-zmq zlib1g-dev wget libcurl4-gnutls-dev bsdmainutils automake curl cmake mingw-w64 libsodium-dev libevent-dev
curl https://sh.rustup.rs -sSf | sh
source $HOME/.cargo/env
rustup target add x86_64-pc-windows-gnu
git clone https://github.com/actioncoininc/action --branch master --single-branch
cd action
./zcutil/fetch-params.sh
./zcutil/build-win.sh -j$(expr $(nproc) - 1)
#This can take some time.
```
**action is experimental and a work-in-progress.** Use at your own risk.

To reset the Action blockchain change into the *~/.komodo/ACTN/* data directory and delete the corresponding files by running `rm -rf blocks chainstate debug.log komodostate db.log`


**This software is based on Zcash which is unfinished and highly experimental.** Use at your own risk.

License
-------
For license information see the file [COPYING](COPYING).

**NOTE TO EXCHANGES:**
https://bitcointalk.org/index.php?topic=1605144.msg17732151#msg17732151
There is a small chance that an outbound transaction will give an error due to mismatched values in wallet calculations. There is a -exchange option that you can run komodod with, but make sure to have the entire transaction history under the same -exchange mode. Otherwise you will get wallet conflicts.

**To change modes:**

a) backup all privkeys (launch komodod with `-exportdir=<path>` and `dumpwallet`)  
b) start a totally new sync including `wallet.dat`, launch with same `exportdir`  
c) stop it before it gets too far and import all the privkeys from a) using `komodo-cli importwallet filename`  
d) resume sync till it gets to chaintip  

For example:
```shell
./komodod -exportdir=/tmp &
./komodo-cli dumpwallet example
./komodo-cli stop
mv ~/.komodo ~/.komodo.old && mkdir ~/.komodo && cp ~/.komodo.old/komodo.conf ~/.komodo.old/peers.dat ~/.komodo
./komodod -exchange -exportdir=/tmp &
./komodo-cli importwallet /tmp/example
```
---


Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
