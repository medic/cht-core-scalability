# Setup of api servers for horizontally scaling cht-core API

## Steps
0. Switch to the `api-horizontal-scalability` branch of `cht-core`
1. Edit the `env_vars-api-server.env` file in this repository.
2. Source the environment variable file. Run `source env_vars-api-server.env`
3. Create a file: `/srv/storage/medic-api/passwd/medic-api` (No need to attach external EBS with data). It should contain the password of the `medic-api` user. This needs to be created for all api-server instances right now. Unless this file exists, api creates its own password and that will invalidate the password for all other horizontally scaled instances. This is a known bug/issue right now. Until that gets solved, this step is a hack that servers to prevent the issue.
3. Run the api-helper container: `sudo -E docker-compose -f docker-compose-archv3-self-hosted-api-helper.yml up -d`. This container will start and set things up and will exit.
4. Run the api-launcher container: `sudo -E docker-compose -f docker-compose-archv3-self-hosted-api-launcher.yml up -d`.

## Notes
If you run into auth related errors, make sure the `medic-api` file under the `/srv/storage/medic-api/passwd/` directory has the correct password.

## CouchDB 3.x Notes
* Use the branch `api-horizontal-scalability-couchdb-3`
