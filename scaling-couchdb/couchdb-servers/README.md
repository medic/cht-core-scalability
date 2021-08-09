# Horizontally Scaling CouchDB for CHT-Core (Working with Clustering)

## Steps

0. Mount the external EBS to `/srv`
1. Edit `env_vars_couchdb_servers.env`
2. Run `source env_vars_couchdb_server.env`
3. Run `Sudo -E docker-compose -f docker-compose-archv3-couchdb-only.yml up -d`
4. Do this in as many instances as you like and setup the cluster using the fauxton cluster configuration settings.
5. Make sure you edit `n` and `q` values. `n` should be equal to the number of nodes you want to use.
6. Notes on how to create a couchdb cluster from [couchdb website](https://docs.couchdb.org/en/stable/config/cluster.html)

## Load Balancer Setup

1. Create a target group that routes traffic to couchdb instances
2. Configure the setup to route traffic based on: `Least outstanding connections`. Because CHT-core replication has long running processes, this is preferrable to simple round robin setup.
3. Configure a listener to the load balancer on port `5985` (Right now, the code doesn't support any other port so this is a requirement). Protocol has to be `https`

## Notes for Couchdb 3.x

Use the docker-compose file `docker-compose-archv3-couchdb-only-couchdb3.yml`
