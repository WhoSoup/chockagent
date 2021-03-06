# ChockAgent

## Deploy an agent

The agent must be run on a machine with a local instance of factomd running (API port 8088 open).

```bash
# Replace AGENT_NAME environment variable value with a uniquely identifiable name
docker pull luciaptech/chockagent
docker run -d \
    --network host \
    --name chockagent \
    -e AGENT_NAME="luciap-testnet" \
    luciaptech/chockagent

# Verify the agent succesfully connected to the coordinator
docker logs chockagent
```

## Run an agent locally (for development)

The easiest way is to run:

```bash
AGENT_NAME="local-chockagent" go run main.go
```

## Build the agent

Running `make` will build the chockagent. Note that the default chockablock endpoint is set at build time (see Makefile).

`docker_push.sh` is a basic script building a chockagent Docker image and pushing it to Docker hub. That script uses the latest git tag to version the image: before publishing an updated image you will need to tag the release (e.g. `git tag v1.1.1`).
