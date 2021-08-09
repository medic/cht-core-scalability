# Main Server Setup for CHT-Core API Scaled Scenario

## Steps

0. Attach external EBS data and moubnt it onto `/srv`
1. Edit `env_vars-haproxy_couchdb.env`
2. Source the env variables: `source env_vars-haproxy_couchdb.env`
3. Start couchdb/haproxy: `sudo -E docker-compose -f docker-compose-archv3-self-hosted-couchdb-haproxy.yml up -d`
4. Go to the other directory and start api server/servers.
5. Come back here and start horti/sentinel: `sudo -E docker-compose -f docker-compose-archv3-self-hosted-horti-sentinel.yml up -d`

