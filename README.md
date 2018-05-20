# Welcome to the EOS Party Testnet

[中文介绍](https://eosfans.io/wiki/eos-party-testnet)

Party is an EOS testnet based on EOSIO Dawn 4.0.

Telegram: https://t.me/EOSTestnet

~~Block Explorer: http://party.eosmonitor.io/~~

## Join the EOS Party Test Network

Anyone can join EOS Party network as BP. Joining the EOS Party test network to become a BP requires the following steps:

- 24-hour server
- Run a node (Recommended Docker)
- Register as BP
- Get votes(You can vote for yourself)

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
    -v /data/eos/nodeos:/root/.local/share/eosio/nodeos \
    -p 8888:8888 \
    -p 9876:9876 \
    eosfans/eos:dawn-v4.0.0 nodeosd.sh
```

Check log:

`docker logs -f --tail=100 party`

## Register an account

Our website is under development, as a temporary plan, you can submit an issue with the EOS public key and producer-name.

## Register as BP

* `docker exec -it party bash`
* `cleos wallet create` Create a default wallet (it is recommended that you save wallet password)
* `cleos wallet import {Private_Key}` Import your private key
* `cleos system regproducer {producer-name} {public key} http://{server_ip}:8888` Register as BP

You should not yet produce a block because you don’t have a ticket.

## Vote for yourself

Mortgage your EOS(Suppose you have 10000):

`cleos system delegatebw {producer-name} {producer-name} '5000.0000 EOS' '5000.0000 EOS' --transfer`

Vote for yourself:
`cleos system voteproducer prods {producer-name} {producer-name}`
