# Bitcoin, LND, Thunderhub, LNBits - K8s


## K8s Port Forwarder
```
kubectl port-forward service/lnbits-service 5000:5000
kubectl port-forward service/thunderhub-service 3000:3000
```

## Useful Commands

### Set variables with pods names
```
BTC_NODE=bitcoind-node-56b7df48d-4krtz
LND_NODE_1=lnd-node-7cc9bfbd4d-bvr7j
```

### Commands
```
kubectl exec -it $LND_NODE_1 -- /bin/sh -c "lncli create"
```

```
kubectl exec -it $BTC_NODE -- /bin/sh -c "bitcoin-cli -rpcport="8332" -rpcuser="a" -rpcpassword="b" createwallet "test""
kubectl exec -it $BTC_NODE -- /bin/sh -c "bitcoin-cli -rpcport="8332" -rpcuser="a" -rpcpassword="b" getnewaddress -addresstype legacy"
kubectl exec -it $BTC_NODE -- /bin/sh -c "bitcoin-cli -rpcport="8332" -rpcuser="a" -rpcpassword="b" -generate 101"
kubectl exec -it $BTC_NODE -- /bin/sh -c "bitcoin-cli -rpcport="8332" -rpcuser="a" -rpcpassword="b" getbalance"
```


```
kubectl exec -it $LND_NODE_1 -- /bin/sh -c "lncli --macaroonpath=\"/root/.lnd/data/chain/bitcoin/regtest/admin.macaroon\" getinfo"
```

```
kubectl exec -it $LND_NODE_1 -- /bin/sh -c "lncli --macaroonpath=\"/root/.lnd/data/chain/bitcoin/regtest/admin.macaroon\" connect 03c64bdf56f0f25f1a3e67ed16df37e1146a4fdbf71792c2d141a0403d8d3cf66b@lnd2-service:9735"
kubectl exec -it $LND_NODE_1 -- /bin/sh -c "lncli --macaroonpath=\"/root/.lnd/data/chain/bitcoin/regtest/admin.macaroon\" listpeers"
```


```
kubectl exec -it $BTC_NODE -- /bin/sh -c "bitcoin-cli -rpcport="8332" -rpcuser="a" -rpcpassword="b" getbalance"
kubectl exec -it $BTC_NODE -- /bin/sh -c "bitcoin-cli -rpcport="8332" -rpcuser="a" -rpcpassword="b" sendtoaddress 2MwN5MnEHLS52z8ej2HBSTVVgkDN5uQFGiH 0.001"
kubectl exec -it $BTC_NODE -- /bin/sh -c "bitcoin-cli -rpcport="8332" -rpcuser="a" -rpcpassword="b" -generate 6"
```

```
kubectl exec -it $LND_NODE_1 -- /bin/sh -c "lncli --macaroonpath=\"/root/.lnd/data/chain/bitcoin/regtest/admin.macaroon\" openchannel 027b401f2134027d41de2857a8d9bdd61dd35eeb2f62249622b05225831e85fd83 100000"
kubectl exec -it $LND_NODE_1 -- /bin/sh -c "lncli --macaroonpath=\"/root/.lnd/data/chain/bitcoin/regtest/admin.macaroon\" channelbalance"
kubectl exec -it $BTC_NODE -- /bin/sh -c "bitcoin-cli -rpcport="8332" -rpcuser="a" -rpcpassword="b" -generate 10"
```

```
kubectl exec -it $LND_NODE_1 -- /bin/sh -c "lncli --macaroonpath=\"/root/.lnd/data/chain/bitcoin/regtest/admin.macaroon\" listchannels"
```


## Faucets
```
https://coinfaucet.eu/en/btc-testnet/
https://bitcoinfaucet.uo1.net/
https://testnet.qc.to/
https://tbtc.bitaps.com/
```

## Lightning Nodes
```
https://htlc.me/
https://faucet.lightning.community/
https://1ml.com/testnet/
```