# Getting Stand Alone Arch V3 Instance Running

## Steps

0. Change values in `env_vars.sh` file and run `source env_vars.env`. This exports required environment variables.
1. Switch to branch `deconstruct-3.10.0` cht-core repository
2. Copy the `docker-compose-archv3-standalone.yml` file in this directory to `cht-core` root directory.
3. Create an image of an instance you want to use for testing
4. Create a new EBS volume from the image
5. Attach EBS volume to the instance.
6. Mount the attached volume to `/srv`
7. From within the `cht-core` directory run `sudo -E docker-compose -f docker-compose-archv3.yml up -d` (You don't need to use sudo if docker is setup not to require `sudo`)


## Notes for CouchDB 3.x

* From step 1 above, use branch `deconstruct-3.10.0-couchdb3` instead of `deconstruct-3.10.0`.
* From step 2 above, use `docker-compose-archv3-standalone-couchdb3.x.yml` instead of `docker-compose-archv3-standalone.yml`
