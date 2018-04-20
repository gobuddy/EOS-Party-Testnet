# Welcome to the EOS Party Testnet

[中文介绍](README-CN.md)

Party is a testing network based on EOSIO Dawn 3.0.

Telegram: https://t.me/EOSTestnet

Block Explorer: http://party.eosmonitor.io/

## Join the EOS Party Test Network

Anyone can join EOS Party network as BP. Joining the EOS Party test network to become a BP requires the following steps:

- 24-hour server
- Run a node (Recommended Docker)
- Apply to us

## Run a node

Make sure your server has Docker installed.

- `mkdir -p /data/eos` Create a directory for your EOS node data store, can also be another directory.
- Copy [config.ini](config.ini) to `/data/eos` and modify:
  - p2p-server-address: Your server ip and p2p port, in general, it is IP:9876
  - agent-name: Organization name
  - private-key: https://nadejde.github.io/eos-token-sale/
  - producer-name: Your BP name.
- Copy [genesis.json](genesis.json) to `/data/eos`.

Then, run:

```
docker run -d \
    --restart=always \
    --name party \
    -v /data/eos:/opt/eosio/bin/data-dir \
    -p 8888:8888 \
    -p 9876:9876 \
    eosfans/eos:3.0.0 nodeosd.sh
```

Check log:

`docker logs -f party`

If you see something like this, it means the connection is successful.

```
push block #129641 from eostea 2018-04-13T04:48:48.500  0001fa699519998bf954cb1a76f97dc9a15d2fb2f4ac6f806b9a795521856bd8 lib: 129628 success
push block #129642 from eostea 2018-04-13T04:48:49.000  0001fa6a03a3046a72fc3f03cf195545d70b58acb959cb0f85b595bd097bd7f8 lib: 129628 success
push block #129643 from eostea 2018-04-13T04:48:49.500  0001fa6b669e131f51962970d6af8eaf7c212cf212e1b676f657f5569194c2c0 lib: 129628 success
push block #129644 from eostea 2018-04-13T04:48:50.000  0001fa6ccb9cf8c83fc34ed2b11f06ffb2c9a320b5e004327bab283d35e82f5c lib: 129628 success
```

## Apply to us

Submit an Issues and include the following information:

- Server Location
- Organisation
-	node ip/domain
- Port (http)
- Port (p2p)
- producer name
- your public key
