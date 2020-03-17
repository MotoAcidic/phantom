[![Travis](https://img.shields.io/travis/MotoAcidic/phantom.svg?style=flat-square)](https://travis-ci.org/MotoAcidic/phantom)
[![Go Report Card](https://goreportcard.com/badge/github.com/MotoAcidic/phantom?style=flat-square)](https://goreportcard.com/report/github.com/MotoAcidic/phantom)

# Phantom-node Daemon

![Phantom Logo](./phantomlogo.png)

Phantom nodes requires no static IP address, no copy of the blockchain, and no proof-of-service. As such, you can run a node on any IP address of your liking: `1.1.1.1` or `8.8.8.8` if you wish. Phantoms also support live hot-swap with currently running nodes, there is no need to re-queue.

The phantom daemon is extremely lightweight allowing you to run hundreds of nodes from a modest machine if you wished. And, possibly most importantly, you can move your currently running masternodes to phantom nodes without restarting since a real IP address is no longer a requirement.

The phantom daemon is custom built wallet designed to replicate only what is required for pre-EVO masternodes to run; it replaces the masternode daemon piece. It does not handle any wallet private keys and has no access to your coins. You will still need a wallet to start your masternodes, but once started, the phatom node system will handle the rest for you.

## Updated
Phantom v0.0.4.2
Original Dev breakcrypto, modified by carsenk & CircuitBreaker & Tfinch

- Added peer caching to peers.db

## Contact information

* email: nexusnow@protonmail.com
* discord: Tfinch
* discord channel: https://discord.gg/eWB5z2E

* email: development@innovacoin.io
* twitter: https://twitter.com/innovacoin
* discord: CircuitBreaker#9827
* Discord Chat: https://discord.gg/hp55tdg

* email: admin@denarius.io
* twitter: https://twitter.com/carsenjk
* discord: Carsen#3333
* Discord Chat: https://discord.gg/UPpQy3n

* email: breakcrypto@gmail.com
* twitter: https://twitter.com/_breakcrypto
* discord: breakcrypto#0011
* discord channel: https://discord.gg/fQPb2ew
* bitcoin talk discussion: https://bitcointalk.org/index.php?topic=5136453.0

# Feature

* Fully self-sufficient
* Minimal memory and disk usage (in the 10s of megabytes vs. gigabytes)
* Hot-swap with live node daemons, no restart required
* Select any IP address, no static IP required
* Auto-load settings from a coinconf.json
* Optionally auto-load bootstrap hashes and peers from Iquidus explorers (more APIs coming soon)
* Epoch timestamp support for high-availability deterministic pings
* Use your existing masternode.conf if you don't want deterministic pings
* Runs on windows, linux, mac, arm, and more.

# A note from the developer

Phantoms have been released to make it easier, and less costly, for masternode supporters to host their own nodes. Masternode hosting companies are free to utilize the phantom system as long as they comply with the terms of the Server Side Public License.

# Quick start

Download a binary release from below. See if there's a coin configuration for the coin you're wishing to use. If not, you'll need to locate the proper settings. There are notes below on where to look or feel free to ask on discord, reddit, or btct. If there is a coin conf for your coin then switching over to phantoms is easy:

```
./phantom -coin_conf="/path/to/coin.conf" -masternode_conf="/path/to/masternode.conf"
```

That's it. You do not need to restart your masternodes, you don't need to change IP addresses, etc. Once the phantom daemon is running, you can disable your masternode daemons, cancel most of VPS subscriptions, and enjoy the savings. You'll know the phantoms are working when you see the active time refresh (can take up to 20 minutes). If that active time doesn't update, restart your daemons and check the settings.

# Downloads

* [Windows AMD64](https://github.com/MotoAcidic/phantom/releases/download/v0.0.4.2/phantom-windows-amd64.exe)
* [Linux AMD64](https://github.com/MotoAcidic/phantom/releases/download/v0.0.4.2/phantom-linux-amd64)
* [OSX AMD64](https://github.com/MotoAcidic/phantom/releases/download/v0.0.4.2/phantom-darwin-amd64)
* [ARMv7 Linux](https://github.com/MotoAcidic/phantom/releases/download/v0.0.4.2/phantom-linux-arm)
* [ARMv6 Pi](https://github.com/MotoAcidic/phantom/releases/download/v0.0.4.2/phantom-linux-armv6)
* [ARMv5 Pi](https://github.com/MotoAcidic/phantom/releases/download/v0.0.4.2/phantom-linux-armv5)

# Setup

The setup is simple: copy your masternode.conf or fortunastake.conf, modify it slightly, launch the phantom executable.

## Masternode.txt setup

Copy your masternode.conf or fortunastake.conf to the same folder as the phantom executable. Rename it to masternode.txt. Remove any comment lines from the top of the file (i.e. delete any line starting with #). At the end of each line add a epoch time ( https://www.unixtimestamp.com ). The epoch timestamp is utilized to allow you to run multiple phantom node setups in a deterministic manner, creating a highly-available configuration.

**Example**

`masternode.conf`
```
# Masternode config file
# Format: alias IP:port masternodeprivkey collateral_output_txid collateral_output_index
mn1 45.50.22.125:17817 73HaYBVUCYjEMeeH1Y4sBGLALQZE1Yc1K64xiqgX37tGBDQL8Xg 2bcd3c84c84f87eaa86e4e56834c92927a07f9e18718810b92e0d0324456a67c 1
```

becomes:

`masternode.txt`
```
mn1 45.50.22.125:17817 73HaYBVUCYjEMeeH1Y4sBGLALQZE1Yc1K64xiqgX37tGBDQL8Xg 2bcd3c84c84f87eaa86e4e56834c92927a07f9e18718810b92e0d0324456a67c 1 1555847365
```

comments removed, epoch timestamp added to the end.

## Run the phantom executable

```
./phantom-linux-amd64 -magicbytes="b73ff4fa" -port=14530 -protocol_number=33500 -magic_message="Innova Signed Message:" -bootstrap_url="https://innova.pro" -max_connections=150 -bootstrap_ips="140.82.16.72:14530"
```

## Coin configurations exist for

* Abet
* CATS
* INN (Innova)
* $PAC
* ANDS
* BEET
* BITG
* CDM
* DEV
* DKPC
* FEIRM
* GBX
* GIC
* HLM
* LPC
* MARC
* MILL
* OMEGA
* PIVX
* POLIS
* PRX
* RAPID
* SINS
* SLX
* SMART
* SPARKS
* SYS
* TELOS
* WGR
* WOLF
* XAP
* XBI
* XLQ
* XZC

There is a coinconf generator included that can auto-generate settings for most masternode coins. Check the `tools/coinconf` directory.

## Available Flags

```
  -bootstrap_hash string
    	Hash to bootstrap the pings with ( top - 12 )
  -bootstrap_ips string
    	IP address to bootstrap the network
  -bootstrap_url string
    	Explorer to bootstrap from.
  -coin_conf
      Name of the file to load the coin information from.
  -daemon_version string
    	The string to use for the sentinel version number (i.e. 1.20.0) (default "0.0.0.0")
  -magic_message string
    	the signing message
  -magic_message_newline
    	add a new line to the magic message (default true)
  -magicbytes string
    	a hex string for the magic bytes
  -masternode_conf
      Name of the file to load the masternode information from.
  -max_connections uint
    	the number of peers to maintain (default 10)
  -port uint
    	the default port number
  -protocol_number uint
    	the protocol number to connect and ping with
  -sentinel_version string
    	The string to use for the sentinel version number (i.e. 1.20.0) (default "0.0.0")
  -user_agent
      The user agent string to connect to remote peers with.
  -db_path
      The destination for peer database storage (default path is ./peers.db)
```

## Building (using Docker)

```
docker run --rm -it -v "$PWD":/go/src/phantom -w /go/src/phantom golang:1.12.4 ./build.sh
```

## Donation Addresses
breakcrypto:

BTC: 151HTde9NgwbMMbMmqqpJYruYRL4SLZg1S

LTC: LhBx1TUyp7wiYuMxjefAGUGZVzuHRtPBA7

DOGE: DBahutcjEAxfwQEW7kzft2y8dhZN2VtcG5
