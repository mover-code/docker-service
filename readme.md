# build for yourself blockchain and expoler for this chain

## First need init chain

```sehll
geth init conf/genesion.json --datadir path 
```

please change this config for yourself

## Then maybe you can run it

```shell
docker-compose up -d
```

## Last start mint

geth attach data/geth.ipc

```sehll
miner.start()
```

## Finally enjoy it
