# Getting CouchDB Scaled Scenario Running for CHT-Core

## Steps

1. Setup Couchdb cluster. Follow the setup outlined under the `couchdb-servers` dir.
2. Setup FQDN for the load balancer configured using route53.
3. Setup the main server. Follow the steps outlined under the `main-server` dir.
4. Setup FQDN for the main server using route53.

## Security Groups

Open ports: `5986, 5984, 4369, 9100, 5985`
