# Main server setup for horizontally Scaled CouchDB for CHT-Core

## Steps

0.1 Switch to branch `deconstruct-3.10.0` cht-core repository
0.2 First get couchdb cluster setup and running by using steps outlined inside `couchdb-servers`
0.3 Save the SSL certificate you'd like to use under directory `/srv/settings/medic-core/nginx/private/default.key` and `/srv/settings/medic-core/nginx/private/default.crt` (No need to attach external EBS containing data as the data sits in the couchdb server instances)
1. Edit `env_vars-master-server.env` file.
2. Run `source env_vars_master-server.env`
3. Edit docker entry scripts for both api and sentinel. Change `get_couchdb_url` function to use `https` instead of `http`
4. Run `sudo -E docker-compose -f docker-compose-archv3-self-hosted-no-couchdb.yml up -d`
5. Log into the `haproxy` container. Use `sudo docker exec -it haproxy /bin/bash`
6. Install `vim` and edit `vim /usr/local/etc/haproxy/haproxy.cfg`. 
    * Change the `server couchdb1 $COUCHDB_HOST:5985` to `server couchdb1 $COUCHDB_HOST:5985 ssl verify none`
    * Change the `server couchdb1 $COUCHDB_HOST:5987` to `server couchdb1 $COUCHDB_HOST:5987 ssl verify none`
6. Exit the haproxy container
7. Restart the haproxy container `sudo docker restart haproxy`

## Notes

If you run into auth related errors, make sure the directory in `/srv/storage/medic-api/passwd/medic-api` contains the correct password for the `medic-api` user. You can experiment with setting this value manually and restarting the `medic-api` container.
