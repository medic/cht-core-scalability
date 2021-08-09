# Scaling CHT-Core API for Arch V3

## Steps

1. Start the main server, couchdb/haproxy in the main server (Steps in the directory)
2. Start the api server/servers (Steps in the directory)
3. Setup load balancer for the API servers.
4. Configure route53 for API servers
5. Start horti/sentinel in the main server (Steps in the directory)
