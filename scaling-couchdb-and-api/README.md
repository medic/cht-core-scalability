# Horizontally scaling both CHT-Core API and CouchDB

## Steps

* Setup couchdb nodes based on the directions under the scaling-couchdb directory.
* Edit env_vars and source them. `source env_vars.env`
* Run haproxy on the main server. `sudo -E docker-compose -f docker-compose-archv3-self-hosted-haproxy-only.yml up -d`
* Make the required changes for `haproxy` to use `https` outlined under the couchdb-scaled scenario.
* Setup the API servers based on the directions under the scaling-api directory.
* Run horti/sentinel based on the direction and docker-compose files under the `api-scaled` scenario.

## Notes

* Note that in this scenario both api and couchdb are behind load balancers.
* It's recommended that you read the README files of the other scenarios in detail before setting this scenario up.
