# lnd events

## Pipelines

* Channel openings / closures `pipelines/channels`
* Routing failures `pipelines/failures`
* Forwarding events `pipelines/forwardings`
* Balancing payments `pipelines/payments`

## Configure

Add `.env` file:

```
LNCLI_OPTS="--rpcserver my-lnd:10009"
ELASTIC_HOST=https://my-elastic:9200"
ELASTIC_USER=elastic
ELASTIC_PASSWORD=secret
```

`set -o allexport; source .env; set +o allexport`

## Run

```
# Sync logs every minute to ~/.lnpipe/logs/
watch -n60 scp root@my-lnd:/root/.lnd/logs/bitcoin/mainnet/lnd.log*" ~/.lnpipe/logs/

# Start all pipelines
logstash --path.settings .
```

## `$HOME/.lnpipe`

Used to store cached data. Get logs from `logs` subfolder.
